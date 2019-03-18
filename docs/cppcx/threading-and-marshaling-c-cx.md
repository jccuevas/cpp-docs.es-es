---
title: Subprocesamiento y cálculo de referencias (C++/CX)
ms.date: 12/30/2016
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
ms.openlocfilehash: c5bce60e564bef490bcfafd6f8559dffe5fd4f1d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751705"
---
# <a name="threading-and-marshaling-ccx"></a>Subprocesamiento y cálculo de referencias (C++/CX)

En la mayoría de los casos, las instancias de clases en tiempo de ejecución de Windows, como objetos de C++ estándares, se pueden acceder desde cualquier subproceso. Dichas clases reciben el nombre de "ágiles". Sin embargo, un número pequeño de clases en tiempo de ejecución de Windows que se incluyen con Windows es no ágiles y debe utilizarse más como objetos COM en los objetos de C++ estándar. No es necesario ser un experto en COM para usar clases no ágiles, pero sí lo es tomar en consideración el modelo de subprocesos de la clase y su comportamiento del cálculo de referencias. En este artículo se proporcionan información y orientación sobre estos escenarios raros en que es necesario usar una instancia de una clase no ágil.

## <a name="threading-model-and-marshaling-behavior"></a>Modelo de subprocesos y comportamiento del cálculo de referencias

Una clase en tiempo de ejecución de Windows puede admitir el acceso simultáneo a subprocesos de varias maneras, según se indica en los dos atributos que se aplican a él:

- El atributo`ThreadingModel` puede tener uno de los valores (STA, MTA o ambos) definidos por la enumeración `ThreadingModel` .

- El atributo`MarshallingBehavior` puede tener uno de los valores (ágil, ninguno o estándar) definidos por la enumeración `MarshallingType` .

El atributo `ThreadingModel` especifica dónde se carga la clase cuando se activa: solo en un contexto de subproceso de interfaz de usuario (STA), solo en un contexto de subproceso en segundo plano (MTA) o en el contexto del subproceso que crea el objeto (ambos). Los valores del atributo `MarshallingBehavior` hacen referencia a cómo se comporta el objeto en los diversos contextos de subprocesos; en la mayoría de los casos, no es necesario comprender estos valores de forma detallada.  De las clases proporcionadas por la API de Windows, aproximadamente un 90 % tienen `ThreadingModel`=Both y `MarshallingType`=Agile. Esto significa que pueden controlar los detalles de subprocesos de bajo nivel de forma transparente y eficaz.   Cuando se utiliza `ref new` para crear una clase “ágil”, puedes llamar a métodos de ella desde tu subproceso de aplicación principal o desde uno o varios subprocesos de trabajo.  Es decir, puedes utilizar una clase ágil, independientemente de si la proporciona Windows o la proporcionan terceros, desde cualquier parte de tu código. No tienes que preocuparte del modelo de subprocesos o del comportamiento del cálculo de referencias de la clase.

## <a name="consuming-windows-runtime-components"></a>Consumo de los componentes de Windows Runtime

Cuando se crea una aplicación plataforma Universal de Windows, es posible que interactúes con componentes tanto ágiles como no ágiles. Cuando interactúas con componentes no ágiles, puedes encontrar la advertencia siguiente.

### <a name="compiler-warning-c4451-when-consuming-non-agile-classes"></a>Advertencia C4451 al usar clases no ágiles del compilador

Por razones diferentes, algunas clases no pueden ser ágiles. Si tienes acceso a instancias de clases no ágiles desde un subproceso de interfaz de usuario y un subproceso en segundo plano, debes tener cuidado para asegurarte de que el comportamiento sea correcto en tiempo de ejecución. El compilador de Visual C++ emite advertencias cuando creas instancias de una clase no ágil en tiempo de ejecución de tu aplicación en el ámbito global o declaras un tipo no ágil como miembro de clase en una clase ref que se marca a sí misma como ágil.

De las clases no ágiles, la más fáciles de tratar son las que tienen `ThreadingModel`=Both y `MarshallingType`=Standard.  Puedes hacer que estas clases sean ágiles con solo usar la clase del asistente `Agile<T>`.   En el ejemplo siguiente se muestra una declaración de un objeto no ágil de tipo `Windows::Security::Credentials::UI::CredentialPickerOptions^`y la advertencia del compilador que se emite como resultado.

```

ref class MyOptions
    {
    public:
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options

        {
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()
            {
                return _myOptions;
            }
        }
    private:
        Windows::Security::Credentials::UI::CredentialPickerOptions^ _myOptions;
    };
```

A continuación se muestra la advertencia que se emite:

> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`

Al agregar una referencia, en el ámbito de miembro o un ámbito global, a un objeto que tiene un comportamiento del cálculo de referencias de "Estándar", el compilador emite una advertencia aconsejándote que incluyas el tipo en que `Platform::Agile<T>`: `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead` Si usa `Agile<T>`, puede utilizar la clase igual que cualquier otra clase ágil. Utiliza `Platform::Agile<T>` en estas circunstancias:

- La variable no ágil se declara en el ámbito global.

- La variable no ágil se declara en el ámbito de clase y existe la posibilidad de que el código utilizado pueda pasar subrepticiamente el puntero, es decir, utilizarlo en un contenedor diferente sin el cálculo de referencias correcto.

Si ninguna de esas condiciones es aplicable, puedes marcar la clase contenedora como no ágil. En otras palabras, se debería directamente almacenar objetos no ágiles solo en clases no ágiles y almacenar los objetos no ágiles mediante Platform:: Agile\<T > en clases ágiles.

En el ejemplo siguiente se muestra cómo debes usar `Agile<T>` para poder omitir sin problemas la advertencia.

```

#include <agile.h>
ref class MyOptions
    {
    public:
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options

        {
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()
            {
                return m_myOptions.Get();
            }
        }
    private:
        Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions^> m_myOptions;

    };
```

Observa que `Agile` no se puede pasar como valor devuelto o parámetro en una clase ref. El método `Agile<T>::Get()` devuelve un "identificador a objeto" (^) que puedes pasar a través de la interfaz binaria de aplicación (ABI) en un método o una propiedad públicos.

En Visual C++, cuando se crea una referencia a una clase en tiempo de ejecución de Windows en un proceso que tiene un comportamiento del cálculo de referencias de "None", el compilador emite la advertencia C4451 pero no sugiere que consideres el uso `Platform::Agile<T>`.  El compilador no puede proporcionar ningún tipo de ayuda más allá de esta advertencia, por lo que tienes la responsabilidad de utilizar la clase correctamente y asegurarte de que el código llame a los componentes STA solo desde el subproceso de interfaz de usuario y a los componentes MTA solo desde un subproceso en segundo plano.

## <a name="authoring-agile-windows-runtime-components"></a>Creación de componentes de Windows en tiempo de ejecución ágiles

Al definir una clase ref en C / c++ / CX, es ágil de forma predeterminada, es decir, tiene `ThreadingModel`= Both y `MarshallingType`= Agile.  Si usa la biblioteca de plantillas C++ de Windows en tiempo de ejecución, se puede crear tu clase ágil derivando de `FtmBase`, que usa el `FreeThreadedMarshaller`.  Si creas una clase que tenga `ThreadingModel`=Both o `ThreadingModel`=MTA, asegúrate de que la clase sea segura para la ejecución de subprocesos.

Puedes modificar el modelo de subprocesos y el comportamiento del cálculo de referencias de una clase ref. Sin embargo, si realizas cambios que presentan la clase como no ágil, debes conocer las implicaciones asociadas a esos cambios.

El ejemplo siguiente muestra cómo aplicar `MarshalingBehavior` y `ThreadingModel` atributos a una clase en tiempo de ejecución en una biblioteca de clases en tiempo de ejecución de Windows. Cuando una aplicación usa el archivo DLL y utiliza la palabra clave `ref new` para activar un objeto de clase `MySTAClass` , el objeto se activa en un contenedor uniproceso y no admite el cálculo de referencias.

```
using namespace Windows::Foundation::Metadata;
using namespace Platform;

[Threading(ThreadingModel::STA)]
[MarshalingBehavior(MarshalingType::None)]
public ref class MySTAClass
{
};
```

Una clase no sellada debe tener valores de configuración de atributos de subprocesos y de cálculo de referencias que permitan al compilador comprobar que las clases derivadas tengan el mismo valor para estos atributos. Si la clase no tiene establecidos de forma explícita esos valores de configuración, el compilador genera un error y no realiza la compilación. Las clases derivadas de una clase no sellada generan un error del compilador en cualquiera de estos casos:

- Los atributos `ThreadingModel` y `MarshallingBehavior` no se definen en la clase derivada.

- Los valores de los atributos `ThreadingModel` y `MarshallingBehavior` de la clase derivada no coinciden con los de la clase base.

El subprocesamiento y serialización información requerida por un componente de Windows en tiempo de ejecución de aplicaciones de terceros se especifica en la información de registro del manifiesto de aplicación para el componente. Se recomienda que use todos los componentes de Windows en tiempo de ejecución de agile. Esto garantiza que el código de cliente pueda llamar al componente desde cualquier subproceso de la aplicación y mejora el rendimiento de dichas llamadas porque son llamadas directas que no tienen cálculo de referencias. Si creas tu clase de esta manera, el código de cliente no tiene que usar `Platform::Agile<T>` para utilizar tu clase.

## <a name="see-also"></a>Vea también

[ThreadingModel](/uwp/api/Windows.Foundation.Metadata.ThreadingModel)<br/>
[MarshallingBehavior](/uwp/api/windows.foundation.metadata.marshalingbehaviorattribute)
