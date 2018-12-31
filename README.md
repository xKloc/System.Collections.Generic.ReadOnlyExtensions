# ReadOnlyExtensions
Expose generic collections as read only interfaces with simple extensions.

## How to Use
Typically you would expose a read-only collection where the class will manage the state internally.

```csharp
public class MyClass
{
    // private list that can be manipulated
    private readonly IList<Item> _items = new List<Item>();

    // public list that is read only
    public IReadOnlyList<Item> Items => _items.AsReadOnly();

    public void AddItem(Item item)
    {
        _items.Add(item);
    }

    public void RemoveItem(Item item)
    {
        _items.Remove(item);
    }
}
```

```csharp
public class MyClass
{
    // private dictionary that can be manipulated
    private readonly IDictionary<int, Item> _items = new Dictionary<int, Item>();

    // public dictionary that is read only
    public IReadOnlyDictionary<int, Item> Items => _items.AsReadOnly();

    public void AddItem(Item item)
    {
        _items[item.Id] = item;
    }

    public void RemoveItem(int itemId)
    {
        _items.Remove(itemId);
    }
}
```

```csharp
public class MyClass
{
    // private collection that can be manipulated
    private readonly ICollection<Item> _items = new HashSet<Item>();

    // public collection that is read only
    public IReadOnlyCollection<Item> Items => _items.AsReadOnly();

    public void AddItem(Item item)
    {
        _items.Add(item);
    }

    public void RemoveItem(Item item)
    {
        _items.Remove(item);
    }
}
```