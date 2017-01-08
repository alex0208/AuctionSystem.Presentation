##  Services

```csharp
    private readonly IRepository<Item> items;
```

```csharp
    public IQueryable<Item> All(int page = 1, int pageSize = GlobalConstants.DefaultPageSize)
    {
        return this.items
                .All()
                .OrderByDescending(i => i.StartDate)
                .Skip((page - 1) * pageSize)
                .Take(pageSize);
    }
```
