---
title: "C&#243;mo: Crear instancias de componentes WRL directamente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# C&#243;mo: Crear instancias de componentes WRL directamente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtenga información sobre cómo utilizar las funciones [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\) [Microsoft::WRL::Make](../windows/make-function.md) y [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) para crear instancias de un componente a partir del módulo que lo define.  
  
 La creación de instancias de componentes directamente permite reducir la sobrecarga cuando no se necesitan generadores de clases u otros mecanismos.  Se pueden crear instancias de un componente directamente en aplicaciones de la [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] y en aplicaciones de escritorio.  
  
 Para obtener información sobre cómo usar [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] para crear un componente básico de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] y para crear instancias del mismo desde una aplicación externa de la [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)], vea [Tutorial: Crear un componente básico de Windows en tiempo de ejecución](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md).  Para obtener información sobre cómo usar [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] para crear un componente COM clásico y para crear instancias del mismo desde una aplicación externa de escritorio, vea [Cómo: Crear un componente COM clásico](../windows/how-to-create-a-classic-com-component-using-wrl.md).  
  
 En este documento se muestran dos ejemplos.  El primer ejemplo utiliza la función `Make` para crear una instancia de un componente.  El segundo ejemplo utiliza la función `MakeAndInitialize` para crear una instancia de un componente que pueden producir errores durante la construcción. \(Puesto que COM suele utilizar valores `HRESULT` en lugar de excepciones para indicar los errores, no se suele producir un tipo COM desde su constructor.  `MakeAndInitialize` permite que un componente valide sus argumentos de construcción mediante el método `RuntimeClassInitialize`\). Ambos ejemplos definen una interfaz básica de registrador e implementan esa interfaz definiendo una clase que escribe mensajes en la consola.  
  
> [!IMPORTANT]
>  No se puede utilizar el operador `new` para crear instancias de los componentes de [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)].  Por tanto, se recomienda usar siempre `Make` o `MakeAndInitialize` para crear instancias de un componente directamente.  
  
### Para crear un componente básico de registrador y crear instancias del mismo  
  
1.  En Visual Studio, cree un proyecto de **Aplicación de consola Win32**.  Asigne nombre al proyecto; por ejemplo, `WRLLogger`.  
  
2.  Agregue un **Archivo MIDL \(.idl\)** al proyecto, asigne al archivo el nombre `ILogger.idl` y después agregue este código:  
  
     [!code-cpp[wrl-logger-make#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]  
  
3.  Utilice el código siguiente para reemplazar el contenido de WRLLogger.cpp.  
  
     [!code-cpp[wrl-logger-make#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]  
  
### Para controlar el error de construcción del componente básico de registrador  
  
1.  Utilice el código siguiente para reemplazar la definición de la clase `CConsoleWriter`.  Esta versión contiene una variable miembro privada de cadena y reemplaza el método `RuntimeClass::RuntimeClassInitialize`.  `RuntimeClassInitialize` produce un error si se produce un error en la llamada a `SHStrDup`.  
  
     [!code-cpp[wrl-logger-makeandinitialize#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]  
  
2.  Utilice el código siguiente para reemplazar la definición de `wmain`.  Esta versión usa `MakeAndInitialize` para crear una instancia del objeto `CConsoleWriter` y comprueba el resultado de `HRESULT`.  
  
     [!code-cpp[wrl-logger-makeandinitialize#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]  
  
## Vea también  
 [Biblioteca de plantillas de Windows Runtime C\+\+ \(WRL\)](../Topic/Windows%20Runtime%20C++%20Template%20Library%20\(WRL\).md)   
 [Microsoft::WRL::Make](../windows/make-function.md)   
 [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)