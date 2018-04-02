# C# Dispose Pattern Example

### 

A public non-virtual `IDisposable.Dispose` implementation that has no parameters.
```C#
public void Dispose()
{
   // Dispose of unmanaged resources.
   Dispose(true);
   // Suppress finalization.
   GC.SuppressFinalize(this);
}
```

A protected virtual `Dispose` method.
```C#
protected virtual void Dispose(bool disposing)
{
    if (!disposed) {
        if (disposing) {
            resourceTobeDisposed.Dispose();
        }
        disposed = true;
    }
}
```

Example of dispose pattern for a derived class.
```C#
class DerivedClass : BaseClass
{
    bool disposed = false;

    protected virtual void Dispose(bool disposing)
    {
        if (!disposed) {
            if (disposing) {
                // dispose unmanagemed resources
                resourceTobeDisposed.Dispose();
            }
            disposed = true;
            // call base class dispose
            base.Dispose(disposing);
        }
    }
}
```

---
References:
- C# documentation [Implementing a Dispose method](https://docs.microsoft.com/en-us/dotnet/standard/garbage-collection/implementing-dispose)
