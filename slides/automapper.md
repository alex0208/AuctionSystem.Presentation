## AutoMapper

#### Before

```csharp
public static Expression<Func<Item, ItemDetailResponseModel>> FromModel
{
	get
	{
		return i => new ItemDetailsResponseModel
		{
			Id = i.Id,
			Name = i.Name
			...
		};
	}
	
}
```
#### Now 
```csharp
var result = this.items
    .All()
    .ProjectTo<ItemsDetailResponseModel>()
    .ToList();

```

```csharp
Mapper.CreateMap<Item, ItemsDetailResponseModel>()
	.ForMember(i => i.TotalItems, opts => opts.MapFrom(i => i.Items.Count));

```