# C# Event Handlers Cheatsheet

### How to define your event args
```C#
public class WorkPerformedEventArgs : System.EventArgs
{
    public int Hours { get; set; }
    public WorkType WorkType { get; set; }
}
```

### How to define your event
```C#
public event EventHandler<WorkPerformedEventArgs> WorkPerformed;
```
*which is similar to…*
```C#
public delegate void WorkPerformedHandler(object sender, WorkPerformedEventArgs e);
```

### How to raise events
```C#
protected virtual void OnWorkPerformed(int hours, WorkType workType)
{
    if (WorkPerformed != null)
    {
        WorkPerformed(10, WorkType.GenerateReports);
    }
}
```

### How to attach event to event handler method

#### Attach event handler to an event
```C#
var worker = new Worker();
worker.WorkPerformed += new EventHandler<WorkPerformedEventArgs>(worker_WorkPerformed);
void worker_WorkPerformed(object sender, WorkPerformedEventArgs e)
{
    // handle the event here...
}
```

#### Attach event handler to an event via C# delegate inference (Recommended)
```C#
var worker = new Worker();
worker.WorkPerformed += worker_WorkPerformed;
void worker_WorkPerformed(object sender, WorkPerformedHandler e)
{
    // handle the event here...
}
```

#### Attach event handler directly to an event using C# anonymous method
```C#
var worker = new Worker();
worker.WorkPerformed += delegate(object sender, WorkPerformedEventArgs e)
{
    // handle the event here...
};
```

#### Attach event handler to an event using lambda (Recommended)
```C#
var worker = new Worker();
worker.WorkPerformed += (sender, e) =>
{
    // handle the event here...
};
```
