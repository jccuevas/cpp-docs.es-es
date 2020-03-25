---
title: 'Cómo: Activar y usar un componente de Windows Runtime mediante WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
ms.openlocfilehash: 7f49c1362bea12576df6039b9e9f0b455cb4fae4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213959"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>Cómo: Activar y usar un componente de Windows Runtime mediante WRL

En este documento se muestra cómo usar la C++ biblioteca de plantillas de Windows Runtime (WRL) para inicializar el Windows Runtime y cómo activar y usar un componente de Windows Runtime.

Para usar un componente, debe adquirir un puntero de interfaz al tipo implementado por el componente. Y dado que la tecnología subyacente del Windows Runtime es el modelo de objetos componentes (COM), debe seguir las reglas COM para mantener una instancia del tipo. Por ejemplo, debe mantener el *recuento de referencias* que determina cuándo se elimina el tipo de la memoria.

Para simplificar el uso de la Windows Runtime, C++ Windows Runtime biblioteca de plantillas proporciona la plantilla de puntero inteligente, [ComPtr\<t >](comptr-class.md), que realiza automáticamente el recuento de referencias. Cuando declare una variable, especifique `ComPtr<`*identificador* *de`>` nombre de interfaz* . Para tener acceso a un miembro de interfaz, aplique el operador de acceso de miembro de flecha (`->`) al identificador.

> [!IMPORTANT]
> Cuando llame a una función de interfaz, pruebe siempre el valor devuelto HRESULT.

## <a name="activating-and-using-a-windows-runtime-component"></a>Activar y usar un componente de Windows Runtime

En los pasos siguientes se usa la interfaz `Windows::Foundation::IUriRuntimeClass` para mostrar cómo crear un generador de activación para un componente Windows Runtime, crear una instancia de ese componente y recuperar un valor de propiedad. También se muestra cómo inicializar el Windows Runtime. A continuación se muestra el ejemplo completo.

> [!IMPORTANT]
> Aunque normalmente se usa la biblioteca C++ de plantillas de Windows Runtime en una aplicación plataforma universal de Windows (UWP), en este ejemplo se usa una aplicación de consola para la ilustración. Las funciones como `wprintf_s` no están disponibles en una aplicación de UWP. Para obtener más información sobre los tipos y las funciones que puede usar en una aplicación de UWP, consulte [funciones de CRT no admitidas en aplicaciones de plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) y [Win32 y com para aplicaciones de UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

#### <a name="to-activate-and-use-a-windows-runtime-component"></a>Para activar y usar un componente de Windows Runtime

1. Incluya (`#include`) cualquier Windows Runtime necesario, Windows Runtime C++ biblioteca de plantillas o C++ encabezados de la biblioteca estándar.

   [!code-cpp[wrl-consume-component#2](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]

   Se recomienda que use la directiva `using namespace` en el archivo .cpp para que el código sea más legible.

2. Inicializa el subproceso en el que se ejecuta la aplicación. Cada aplicación debe inicializar su modelo de subprocesos y subprocesos. En este ejemplo se usa la clase [Microsoft:: WRL:: wrappers:: RoInitializeWrapper](roinitializewrapper-class.md) para inicializar el Windows Runtime y se especifica [RO_INIT_MULTITHREADED](/windows/win32/api/roapi/ne-roapi-ro_init_type) como modelo de subprocesos. La clase `RoInitializeWrapper` llama a `Windows::Foundation::Initialize` en la construcción y `Windows::Foundation::Uninitialize` cuando se destruye.

   [!code-cpp[wrl-consume-component#3](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]

   En la segunda instrucción, el operador [RoInitializeWrapper:: HRESULT](roinitializewrapper-class.md#hresult) devuelve el `HRESULT` de la llamada a `Windows::Foundation::Initialize`.

3. Cree un *generador de activación* para la interfaz `ABI::Windows::Foundation::IUriRuntimeClassFactory`.

   [!code-cpp[wrl-consume-component#4](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]

   El Windows Runtime usa nombres completos para identificar tipos. El parámetro `RuntimeClass_Windows_Foundation_Uri` es una cadena proporcionada por el Windows Runtime y contiene el nombre de clase en tiempo de ejecución necesario.

4. Inicialice una variable [Microsoft:: WRL:: wrappers:: HString](hstring-class.md) que represente el URI `"https://www.microsoft.com"`.

   [!code-cpp[wrl-consume-component#6](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]

   En el Windows Runtime, no se asigna memoria para una cadena que utilizará el Windows Runtime. En su lugar, el Windows Runtime crea una copia de la cadena en un búfer que mantiene y utiliza para las operaciones y, a continuación, devuelve un identificador al búfer que creó.

5. Use el Factory Method `IUriRuntimeClassFactory::CreateUri` para crear un objeto `ABI::Windows::Foundation::IUriRuntimeClass`.

   [!code-cpp[wrl-consume-component#7](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]

6. Llame al método `IUriRuntimeClass::get_Domain` para recuperar el valor de la propiedad `Domain`.

   [!code-cpp[wrl-consume-component#8](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]

7. Imprima el nombre de dominio en la consola y devuelva. Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.

   [!code-cpp[wrl-consume-component#9](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]

   La función [WindowsGetStringRawBuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer) recupera el formato Unicode subyacente de la cadena de URI.

Este es el ejemplo completo:

[!code-cpp[wrl-consume-component#1](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]

## <a name="compiling-the-code"></a>Compilar el código

Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `wrl-consume-component.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

`cl.exe wrl-consume-component.cpp runtimeobject.lib`

## <a name="see-also"></a>Consulte también

[Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](windows-runtime-cpp-template-library-wrl.md)
