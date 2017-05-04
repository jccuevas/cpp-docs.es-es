---
title: "Subprocesamiento y c&#225;lculo de referencias (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4451"
helpviewer_keywords: 
  - "problemas con el subprocesamiento, C++/CX"
  - "agilidad, C++/CX"
  - "C++/CX, problemas con el subprocesamiento"
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
caps.latest.revision: 17
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 17
---
# Subprocesamiento y c&#225;lculo de referencias (C++/CX)
En la gran mayoría de los casos, se puede tener acceso desde cualquier subproceso a instancias de clases de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)], como objetos de C\+\+ estándar. Dichas clases reciben el nombre de "ágiles". Sin embargo, un pequeño número de clases de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] que se proporcionan con Windows son no ágiles y deben utilizarse más como objetos COM que como objetos de C\+\+ estándar. No es necesario ser un experto en COM para usar clases no ágiles, pero sí lo es tomar en consideración el modelo de subprocesos de la clase y su comportamiento del cálculo de referencias. En este artículo se proporcionan información y orientación sobre estos escenarios raros en que es necesario usar una instancia de una clase no ágil.  
  
## Modelo de subprocesos y comportamiento del cálculo de referencias  
 Una clase de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] puede admitir el acceso simultáneo a subprocesos de varias maneras, según lo indican dos atributos que se aplican a ella:  
  
-   El atributo `ThreadingModel` puede tener uno de los valores \(STA, MTA o ambos\) definidos por la enumeración `ThreadingModel`.  
  
-   El atributo `MarshallingBehavior` puede tener uno de los valores \(ágil, ninguno o estándar\) definidos por la enumeración `MarshallingType`.  
  
 El atributo `ThreadingModel` especifica dónde se carga la clase cuando se activa: solo en un contexto de subproceso de interfaz de usuario \(STA\), solo en un contexto de subproceso en segundo plano \(MTA\) o en el contexto del subproceso que crea el objeto \(ambos\). Los valores del atributo `MarshallingBehavior` hacen referencia a cómo se comporta el objeto en los diversos contextos de subprocesos; en la mayoría de los casos, no es necesario comprender estos valores de forma detallada.  De las clases proporcionadas por la API de Windows, aproximadamente un 90 % tienen `ThreadingModel`\=Both y `MarshallingType`\=Agile. Esto significa que pueden controlar los detalles de subprocesos de bajo nivel de forma transparente y eficaz.   Cuando se utiliza `ref new` para crear una clase “ágil”, puedes llamar a métodos de ella desde tu subproceso de aplicación principal o desde uno o varios subprocesos de trabajo.  Es decir, puedes utilizar una clase ágil, independientemente de si la proporciona Windows o la proporcionan terceros, desde cualquier parte de tu código. No tienes que preocuparte del modelo de subprocesos o del comportamiento del cálculo de referencias de la clase.  
  
## Utilizar componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]  
 Cuando creas una aplicación de [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)], es posible que interactúes con componentes tanto ágiles como no ágiles. Cuando interactúas con componentes no ágiles, puedes encontrar la advertencia siguiente.  
  
### Advertencia del compilador cuando se utilizan clases no ágiles \(C4451\)  
 Por razones diferentes, algunas clases no pueden ser ágiles. Si tienes acceso a instancias de clases no ágiles desde un subproceso de interfaz de usuario y un subproceso en segundo plano, debes tener cuidado para asegurarte de que el comportamiento sea correcto en tiempo de ejecución. El compilador de Visual C\+\+ emite advertencias cuando creas instancias de una clase no ágil en tiempo de ejecución de tu aplicación en el ámbito global o declaras un tipo no ágil como miembro de clase en una clase ref que se marca a sí misma como ágil.  
  
 De las clases no ágiles, la más fáciles de tratar son las que tienen `ThreadingModel`\=Both y `MarshallingType`\=Standard.  Puedes hacer que estas clases sean ágiles con solo usar la clase auxiliar `Agile<T>`.   En el ejemplo siguiente se muestra una declaración de un objeto no ágil de tipo `Windows::Security::Credentials::UI::CredentialPickerOptions^` y la advertencia del compilador que se emite como resultado.  
  
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
  
 Cuando agregas una referencia, en el ámbito de miembro o en el ámbito global, a un objeto que tiene un comportamiento del cálculo de referencias de “Standard”, el compilador emite una advertencia aconsejándote que incluyas el tipo en `Platform::Agile<T>`: `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`. Si utilizas `Agile<T>`, puedes utilizar la clase del mismo modo que cualquier otra clase ágil. Utiliza `Platform::Agile<T>` en estas circunstancias:  
  
-   La variable no ágil se declara en el ámbito global.  
  
-   La variable no ágil se declara en el ámbito de clase y existe la posibilidad de que el código utilizado pueda pasar subrepticiamente el puntero, es decir, utilizarlo en un contenedor diferente sin el cálculo de referencias correcto.  
  
 Si ninguna de esas condiciones es aplicable, puedes marcar la clase contenedora como no ágil. Es decir, debe almacenar los objetos no ágiles solo en clases no ágiles y almacenar los objetos no ágiles mediante Platform::Agile\<T\> en clases ágiles.  
  
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
  
 Observa que `Agile` no se puede pasar como valor devuelto o parámetro en una clase ref. El método `Agile<T>::Get()` devuelve un "identificador a objeto" \(^\) que puedes pasar a través de la interfaz binaria de aplicación \(ABI\) en un método o una propiedad públicos.  
  
 En Visual C\+\+, si creas una referencia a una clase de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] en proceso que tenga un comportamiento del cálculo de referencias de “None”, el compilador emite la advertencia C4451 pero no sugiere que consideres el uso de `Platform::Agile<T>`.  El compilador no puede proporcionar ningún tipo de ayuda más allá de esta advertencia, por lo que tienes la responsabilidad de utilizar la clase correctamente y asegurarte de que el código llame a los componentes STA solo desde el subproceso de interfaz de usuario y a los componentes MTA solo desde un subproceso en segundo plano.  
  
## Crear componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] ágiles  
 Cuando defines una clase ref en [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)], es ágil de forma predeterminada, es decir, tiene `ThreadingModel`\=Both y `MarshallingType`\=Agile.  Si usas [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)], puedes crear tu clase ágil derivando de `FtmBase`, que usa `FreeThreadedMarshaller`.  Si creas una clase que tenga `ThreadingModel`\=Both o `ThreadingModel`\=MTA, asegúrate de que la clase sea segura para la ejecución de subprocesos. Para más información, vea [Crear y consumir objetos \(WRL\)](http://msdn.microsoft.com/es-es/d5e42216-e888-4f1f-865a-b5ccd0def73e).  
  
 Puedes modificar el modelo de subprocesos y el comportamiento del cálculo de referencias de una clase ref. Sin embargo, si realizas cambios que presentan la clase como no ágil, debes conocer las implicaciones asociadas a esos cambios.  
  
 En el ejemplo siguiente se muestra la forma de aplicar los atributos `MarshalingBehavior` y `ThreadingModel` a una clase en tiempo de ejecución en una biblioteca de clases de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]. Cuando una aplicación usa el archivo DLL y utiliza la palabra clave `ref new` para activar un objeto de clase `MySTAClass`, el objeto se activa en un contenedor uniproceso y no admite el cálculo de referencias.  
  
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
  
-   Los atributos `ThreadingModel` y `MarshallingBehavior` no se definen en la clase derivada.  
  
-   Los valores de los atributos `ThreadingModel` y `MarshallingBehavior` de la clase derivada no coinciden con los de la clase base.  
  
 La información de subprocesos y de cálculo de referencias requerida por un componente de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] de terceros se especifica en la información de registro del manifiesto de aplicación para el componente. Recomendamos que hagas que todos los componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] sean ágiles. Esto garantiza que el código de cliente pueda llamar al componente desde cualquier subproceso de la aplicación y mejora el rendimiento de dichas llamadas porque son llamadas directas que no tienen cálculo de referencias. Si creas tu clase de esta manera, el código de cliente no tiene que usar `Platform::Agile<T>` para utilizar tu clase.  
  
## Vea también  
 [\(NOTINBUILD\) Temas avanzados](http://msdn.microsoft.com/es-es/1ccff0cf-a6cc-47ef-a05f-eba6307b3ced)   
 [ThreadingModel](http://msdn.microsoft.com/library/windows/apps/xaml/windows.foundation.metadata.threadingmodel.aspx)   
 [MarshallingBehavior](http://msdn.microsoft.com/library/windows/apps/xaml/windows.foundation.metadata.marshalingbehaviorattribute.aspx)