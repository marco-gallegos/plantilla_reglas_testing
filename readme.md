# Reglas del proyecto

## Testing

Reglas relacionadaas a como se deben implementar las pruebas unitarias para este proyecto.

### Caracteristicas (DDD)

* Framework Version : netcore 3.1
  * [Documentacion](https://docs.microsoft.com/en-us/dotnet/fundamentals/)
* Libreria Testing :  Native Unit Test Project -> mstest
  * [Documentacion](https://docs.microsoft.com/en-us/dotnet/core/testing/unit-testing-with-mstest)
* Patrones de diseño a considerar
  * DDD 
  * Repository
  * CQRS
  * Dependency Injection

### Recursos

* implementar lista

### Reglas

Este proyecto de unit testing sigue una estrategia de replicacion de ruta y namespace para el unit testing, es decir se debe crear un espejo de directorios y de namespace con la inflexion de aregar un profijo de "Test" en el namespace y la clase. tambien es necesario crear por lo menos 3 pruebas para cada caracteristica a testear.

### Tips y Trucos

#### Crear proyecto de prueba unitaria netcore y agregarlo al proyecto existente

Este apartado es para agregar un proyecto de pruebas unitarias a una solucion existente:

```shell
dotnet new mstest -o "project name" -f netcoreapp3.1

dotnet sln ".sln filename" add 'project name'/".csproj filename"
```

### Ejemplos

#### Ejemplo de un test unitario simple:

```c#
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace Tests
{
    [TestClass]
    public class UnitTest1
    {
        [TestMethod]
        public void TestMethod1()
        {
            Assert.AreEqual(true, true);
        }
        
        [TestMethod]
        public void nueva()
        {
            Assert.AreEqual(true, true);
        }
    }
}
```

#### Ejemplo de juguete de un test unitario en DDD:

suponiendo la jerarquia siguiente:

* Api.Domain
  * Entities
    * UserEntity.cs
* Api.Aplication
* Api.Infrastructure

con el siguiente contenido en user.cs

```c#
namespace Api.Domain.Entities {
    public class UserEntity : BaseEntity {
        public string Name { get; set; }
        public string Email { get; set; }
    }
}
```

dbemos crear la siguiente estructura dentro de nuestro proyecto de test:

* Api.Domain
  * Entities
    * UserEntity.cs
* Api.Aplication
* Api.Infrastructure

con el siguiente contenido en user.cs

```c#
namespace Test.Api.Domain.Entities {
    [TestClass]
    public class TestUserEntity
    {
        [TestMethod]
        public void TestCorrect()
        {
            //Implementar codigo testing
            Assert.AreEqual(true, true);
        }
        
        [TestMethod]
        public void TestBad()
        {
            //Implementar codigo testing
            Assert.AreEqual(true, true);
        }
        
        [TestMethod]
        public void TestRealorRandom()
        {
            //Implementar codigo testing
            Assert.AreEqual(true, true);
        }
    }
}
```
