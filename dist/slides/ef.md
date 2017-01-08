## Entity Framework 6

```csharp
	// AuctionSystemDbContext
    public virtual IDbSet<Item> Items { get; set; }
    public virtual IDbSet<Bid> Bids { get; set; }
    public virtual IDbSet<Category> Categories { get; set; }

    public static AuctionSystemDbContext Create()
    {
        return new AuctionSystemDbContext();
    }
```

```csharp
	// DatabaseConfig
    public static void Initialize()
    {
        Database.SetInitializer(
      	  new MigrateDatabaseToLatestVersion<AuctionSystemDbContext, Configuration>());

        AuctionSystemDbContext.Create().Database.Initialize(true);
    }
```