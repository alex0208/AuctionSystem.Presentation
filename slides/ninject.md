## Ninject

#### Before
```csharp
private readonly IItemsService items;

public ItemsController(IItemsService itemsService)
{
	var db = new AuctionSystemDbContext();
	this.items = itemsService;
}
```
```csharp
public ItemsService()
{
	var db = new AuctionSystemDbContext();
	this.itmes = new EfGenericRepository<Item>(db);

}
```
#### Now
```csharp
    private static void RegisterServices(IKernel kernel)
    {
	    kernel.Bind(b => b.From(Assemblies.Services)
          .SelectAllClasses()
          .BindDefaultInterface());
    }
```
