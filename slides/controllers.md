##  Controllers

```csharp
    private readonly IItemsService items;
```

#### GET
```csharp
    public IHttpActionResult Get(int id)
    {
        var result = this.items
            .All()
            .ProjectTo<ItemsDetailResponseModel>()
            .FirstOrDefault(i => i.Id == id);

        return this.Ok(result);
    }
```

#### POST
```csharp
    public IHttpActionResult Post(SaveItemRequestModel model)
    {
        if (!this.ModelState.IsValid)
        {
            return this.BadRequest(this.ModelState);
        }

        var createdItemId = this.items.Add(...);

        return this.Ok(createdItemId);
    }
```