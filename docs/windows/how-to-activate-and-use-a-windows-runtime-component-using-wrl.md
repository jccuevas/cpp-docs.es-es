---
title: "C&#243;mo: Activar y usar un componente de Windows en tiempo de ejecuci&#243;n mediante WRL | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Activar y usar un componente de Windows en tiempo de ejecuci&#243;n mediante WRL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este documento se muestra cómo utilizar [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\) para inicializar [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] y cómo provocar y utilizar un componente de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] .  
  
> [!NOTE]
>  Este ejemplo produce un componente integrado de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] .  Para obtener información sobre cómo crear dispone del componente que puede generar de la misma manera, vea [Tutorial: Crear un componente básico de Windows en tiempo de ejecución](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md).  
  
 Para utilizar un componente, debe adquirir un puntero de interfaz al tipo implementado por el componente.  Y porque la tecnología subyacente de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] es el modelo de objetos componentes \(COM\), debe seguir reglas COM para mantener una instancia del tipo.  Por ejemplo, debe mantener *el recuento de referencias* que determina cuando elimine el tipo de memoria.  
  
 Para simplificar el uso de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)], [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] proporciona la plantilla de puntero inteligente, [ComPtr\<T\>](../windows/comptr-class.md), que realizan automáticamente el recuento de referencias.  Cuando declara una variable, especifique `ComPtr<`*interface\-name*`>` *identifier*.  Para tener acceso a un miembro de interfaz, aplique el operador de acceso a miembros de flecha \(`->`\) al identificador.  
  
> [!IMPORTANT]
>  Cuando se llama a una función de interfaz, siempre pruebe el valor devuelto de `HRESULT` .  
  
## El provocar y Utilizar un componente en tiempo de ejecución de Windows  
 Los pasos siguientes utilizan la interfaz de `Windows::Foundation::IUriRuntimeClass` para mostrar cómo crear un generador de activación para un componente de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] , cree una instancia de ese componente, y recuperar un valor de propiedad.  También se muestra cómo inicializar [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  A continuación se muestra el ejemplo completo.  
  
> [!IMPORTANT]
>  Aunque use normalmente [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] en una aplicación de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] , este ejemplo utiliza una aplicación de consola a la ilustración.  Las funciones como `wprintf_s` no están disponibles de una aplicación de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] .  Para obtener más información sobre los tipos y funciones que puede utilizar en una aplicación de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] , vea [Funciones CRT no compatibles con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx) y [Win32 y COM para las aplicaciones del almacén de Windows](http://msdn.microsoft.com/library/windows/apps/br205757.aspx).  
  
#### Para generar y utilizar un componente en tiempo de ejecución de Windows  
  
1.  Incluya \(`#include`\) cualquier encabezado de biblioteca de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)], [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] o estándar de C\+\+ necesario.  
  
     [!code-cpp[wrl-consume-component#2](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]  
  
     Se recomienda que use la directiva `using namespace` en el archivo .cpp para que el código sea más legible.  
  
2.  Inicializa el subproceso en el que se ejecuta la aplicación.  Cada aplicación debe inicializar el subproceso y modelo de subprocesos.  Este ejemplo utiliza la clase de [Microsoft::WRL::Wrappers::RoInitializeWrapper](../Topic/RoInitializeWrapper%20Class.md) para inicializar [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] y especifica [RO\_INIT\_MULTITHREADED](http://msdn.microsoft.com/library/windows/apps/br224661.aspx) como el modelo de subprocesos.  La clase de `RoInitializeWrapper` llama `Windows::Foundation::Initialize` en la construcción, y `Windows::Foundation::Uninitialize` cuando se destruye.  
  
     [!code-cpp[wrl-consume-component#3](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]  
  
     En la segunda instrucción, el operador de [RoInitializeWrapper::HRESULT](../windows/roinitializewrapper-hresult-parens-operator.md) devuelve `HRESULT` de la llamada a `Windows::Foundation::Initialize`.  
  
3.  Cree *un generador de activación* para la interfaz de `ABI::Windows::Foundation::IUriRuntimeClassFactory` .  
  
     [!code-cpp[wrl-consume-component#4](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]  
  
     [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] utiliza nombres completos para identificar tipos.  El parámetro de `RuntimeClass_Windows_Foundation_Uri` es una cadena proporcionada por [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] y contiene el nombre de clase necesario en tiempo de ejecución.  
  
4.  Inicializa una variable de [Microsoft::WRL::Wrappers::HString](../windows/hstring-class.md) que representa el URI `"http://www.microsoft.com"`.  
  
     [!code-cpp[wrl-consume-component#6](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]  
  
     En [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)], no asigna memoria para una cadena que [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] utilice.  En su lugar, [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] crea una copia de la cadena en un búfer que mantiene y utilice para las operaciones, y devuelve un identificador al búfer que creó.  
  
5.  Utilice el método del generador de `IUriRuntimeClassFactory::CreateUri` para crear un objeto de `ABI::Windows::Foundation::IUriRuntimeClass` .  
  
     [!code-cpp[wrl-consume-component#7](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]  
  
6.  Llame al método de `IUriRuntimeClass::get_Domain` para recuperar el valor de la propiedad de `Domain` .  
  
     [!code-cpp[wrl-consume-component#8](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]  
  
7.  Imprimir el nombre de dominio en la consola y vuelva.  Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.  
  
     [!code-cpp[wrl-consume-component#9](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]  
  
     [WindowsGetStringRawBuffer](http://msdn.microsoft.com/library/windows/apps/br224636.aspx) La función recupera el formulario subyacente Unicode de cadena URI.  
  
 A continuación se muestra el ejemplo completo:  
  
 [!code-cpp[wrl-consume-component#1](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]  
  
## Compilar el código  
 Para compilar el código, cópielo y péguelo en un proyecto de Visual Studio, o péguelo en un archivo denominado `wrl-consume-component.cpp` y después se ejecute el siguiente comando en una ventana de símbolo del sistema de Visual Studio.  
  
 **cl.exe wrl\-consume\-component.cpp runtimeobject.lib**  
  
## Vea también  
 [Biblioteca de plantillas de Windows Runtime C\+\+ \(WRL\)](../Topic/Windows%20Runtime%20C++%20Template%20Library%20\(WRL\).md)