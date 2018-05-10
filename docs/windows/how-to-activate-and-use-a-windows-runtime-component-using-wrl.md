---
title: 'Cómo: activar y usar un componente de tiempo de ejecución de Windows mediante WRL | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50c37438bf3a840f57119245b845d0b94f1873db
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>Cómo: Activar y usar un componente de Windows Runtime mediante WRL
Este documento muestra cómo usar la biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución para inicializar el Runtime de Windows y cómo activar y usar un componente en tiempo de ejecución de Windows.  
  
 Para usar un componente, debe adquirir un puntero de interfaz para el tipo que se implementa en el componente. Y dado que la tecnología subyacente de Windows Runtime es el modelo de objetos componentes (COM), debe seguir las reglas de COM para mantener una instancia del tipo. Por ejemplo, debe mantener la *recuento de referencias* que determina cuándo se elimina el tipo de la memoria.  
  
 Para simplificar el uso de Windows Runtime, biblioteca de plantillas de C++ de Windows en tiempo de ejecución proporciona la plantilla de puntero inteligente, [ComPtr\<T >](../windows/comptr-class.md), que realiza automáticamente recuento de referencias. Cuando se declara una variable, especifique `ComPtr<` *nombre de la interfaz* `>` *identificador*. Para obtener acceso a un miembro de interfaz, aplicar el operador de acceso a miembros de flecha (`->`) al valor del identificador.  
  
> [!IMPORTANT]
>  Cuando se llama a una función de la interfaz, pruebe siempre la `HRESULT` valor devuelto.  
  
## <a name="activating-and-using-a-windows-runtime-component"></a>Activación y el uso de un componente de tiempo de ejecución de Windows  
 Los siguientes pasos se usa el `Windows::Foundation::IUriRuntimeClass` interfaz para mostrar cómo crear un generador de activación de un componente en tiempo de ejecución de Windows, cree una instancia de dicho componente y recuperar un valor de propiedad. También se muestra cómo inicializar el tiempo de ejecución de Windows. A continuación se muestra el ejemplo completo.  
  
> [!IMPORTANT]
>  Aunque normalmente se utiliza la biblioteca de plantillas de C++ de Windows en tiempo de ejecución en una aplicación de plataforma Universal de Windows (UWP), en este ejemplo se utiliza una aplicación de consola a modo de ilustración. Las funciones como `wprintf_s` no están disponibles en una aplicación de UWP. Para obtener más información sobre los tipos y funciones que pueden usar en una aplicación UWP, vea [funciones de CRT no admitidas en aplicaciones de la plataforma Universal de Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) y [Win32 y COM para aplicaciones UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).  
  
#### <a name="to-activate-and-use-a-windows-runtime-component"></a>Para activar y usar un componente en tiempo de ejecución de Windows  
  
1.  Incluir (`#include`) los necesarios en tiempo de ejecución de Windows, biblioteca de plantillas de C++ de Windows en tiempo de ejecución o encabezados de la biblioteca estándar de C++.  
  
     [!code-cpp[wrl-consume-component#2](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]  
  
     Se recomienda que use la directiva `using namespace` en el archivo .cpp para que el código sea más legible.  
  
2.  Inicializar el subproceso en el que se ejecuta la aplicación. Deben inicializar todas las aplicaciones de su subproceso y el modelo de subprocesos. Este ejemplo se utiliza la [Microsoft::WRL::Wrappers::RoInitializeWrapper](../windows/roinitializewrapper-class.md) para inicializar el Runtime de Windows de clase y especifica [RO_INIT_MULTITHREADED](http://msdn.microsoft.com/library/windows/apps/br224661.aspx) como el modelo de subprocesos. El `RoInitializeWrapper` clase llamadas `Windows::Foundation::Initialize` en la construcción, y `Windows::Foundation::Uninitialize` cuando se destruye.  
  
     [!code-cpp[wrl-consume-component#3](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]  
  
     En la segunda instrucción, la [RoInitializeWrapper::HRESULT](../windows/roinitializewrapper-hresult-parens-operator.md) operador devuelve el `HRESULT` de la llamada a `Windows::Foundation::Initialize`.  
  
3.  Crear un *generador de activación* para el `ABI::Windows::Foundation::IUriRuntimeClassFactory` interfaz.  
  
     [!code-cpp[wrl-consume-component#4](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]  
  
     El tiempo de ejecución de Windows utiliza nombres completos para identificar tipos. El `RuntimeClass_Windows_Foundation_Uri` parámetro es una cadena que se proporciona en tiempo de ejecución de Windows y contiene el nombre de clase en tiempo de ejecución.  
  
4.  Inicializar un [Microsoft::WRL::Wrappers::HString](../windows/hstring-class.md) variable que representa el URI `"http://www.microsoft.com"`.  
  
     [!code-cpp[wrl-consume-component#6](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]  
  
     En el tiempo de ejecución de Windows, no asignar memoria para una cadena que se va a usar el tiempo de ejecución de Windows. En su lugar, el tiempo de ejecución de Windows crea una copia de la cadena en un búfer que mantiene y utiliza para las operaciones y, a continuación, devuelve un identificador para el búfer que se crea.  
  
5.  Use la `IUriRuntimeClassFactory::CreateUri` factory method para crear un `ABI::Windows::Foundation::IUriRuntimeClass` objeto.  
  
     [!code-cpp[wrl-consume-component#7](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]  
  
6.  Llame a la `IUriRuntimeClass::get_Domain` método para recuperar el valor de la `Domain` propiedad.  
  
     [!code-cpp[wrl-consume-component#8](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]  
  
7.  Imprimir el nombre de dominio en la consola y devolver. Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.  
  
     [!code-cpp[wrl-consume-component#9](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]  
  
     El [WindowsGetStringRawBuffer](http://msdn.microsoft.com/library/windows/apps/br224636.aspx) función recupera el formulario de Unicode subyacente de la cadena URI.  
  
 Aquí se muestra el ejemplo completo:  
  
 [!code-cpp[wrl-consume-component#1](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo que se denomina `wrl-consume-component.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe component.cpp consumir wrl runtimeobject.lib**  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)