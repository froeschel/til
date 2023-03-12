# Static Factory Methods

Normally, we use constructors to initialize new objects. This can be seen in the following example.

```
internal class Car
{
    private string _type;
    private string _model;
    private string _brand;

    public Car(string type, string model, string brand)
    {
        _type = type;
        _model = model;
        _brand = brand;
    }
}
```

However, a static factory method could be a better situation in some cases. A static factory method for initializing an object can look like that:

```
public static Car CreateSuvFromVolvo(string typeOfCar, string carModel, string carBrand)
{
    return new Car(typeOfCar, carModel, carBrand);
}
```

Using a static factory method will have some advantages. The code will be easier to read, because we clearly express what the intent of the method is. It also gets easier to add some validation and error handling, so there is more control when initializing new objects. 