---
title: 'Cómo: crear instancias de componentes WRL directamente | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 40904f8379d1a11d26c29af2340fa4adb24f12e0
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39568821"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>Cómo: Crear instancias de componentes WRL directamente
Aprenda a usar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución (WRL)[Microsoft::WRL::Make](../windows/make-function.md) y [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) funciones para crear instancias de un componente desde el módulo que lo define.  
  
 La creación de instancias de componentes directamente permite reducir la sobrecarga cuando no se necesitan generadores de clases u otros mecanismos. Puede crear una instancia de un componente directamente en ambas aplicaciones de plataforma Universal de Windows y aplicaciones de escritorio.  
  
Para obtener información sobre cómo usar la biblioteca de plantillas C++ de Windows en tiempo de ejecución para crear un componente COM clásico y crear una instancia de una aplicación de escritorio externa, consulte [Cómo: crear un componente COM clásico](../windows/how-to-create-a-classic-com-component-using-wrl.md).  
  
 En este documento se muestran dos ejemplos. El primer ejemplo utiliza la función `Make` para crear una instancia de un componente. El segundo ejemplo utiliza la función `MakeAndInitialize` para crear una instancia de un componente que pueden producir errores durante la construcción. (Dado que COM suele utilizar valores HRESULT, en lugar de excepciones, para indicar errores, un tipo COM no se suele produce desde su constructor. `MakeAndInitialize` permite que un componente valide sus argumentos de construcción mediante el método `RuntimeClassInitialize`). Ambos ejemplos definen una interfaz básica de registrador e implementan esa interfaz definiendo una clase que escribe mensajes en la consola.  
  
> [!IMPORTANT]
>  No puede usar el **nuevo** operador para crear instancias de componentes de la biblioteca de plantillas C++ de Windows en tiempo de ejecución. Por tanto, se recomienda usar siempre `Make` o `MakeAndInitialize` para crear instancias de un componente directamente.  
  
### <a name="to-create-and-instantiate-a-basic-logger-component"></a>Para crear un componente básico de registrador y crear instancias del mismo  
  
1.  En Visual Studio, cree un **aplicación de consola Win32** proyecto. Nombre del proyecto, por ejemplo, `WRLLogger`.  
  
2.  Agregar un **archivo Midl (.idl)** al proyecto, asigne el nombre del archivo `ILogger.idl`y, a continuación, agregue este código:  
  
     [!code-cpp[wrl-logger-make#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]  
  
3.  Utilice el código siguiente para reemplazar el contenido de WRLLogger.cpp.  
  
     [!code-cpp[wrl-logger-make#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]  
  
### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>Para controlar el error de construcción del componente básico de registrador  
  
1.  Utilice el código siguiente para reemplazar la definición de la clase `CConsoleWriter`. Esta versión contiene una variable miembro privada de cadena y reemplaza el método `RuntimeClass::RuntimeClassInitialize`. `RuntimeClassInitialize` produce un error si se produce un error en la llamada a `SHStrDup`.  
  
     [!code-cpp[wrl-logger-makeandinitialize#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]  
  
2.  Utilice el código siguiente para reemplazar la definición de `wmain`. Esta versión usa `MakeAndInitialize` para crear una instancia del objeto `CConsoleWriter` y comprueba el resultado de `HRESULT`.  
  
     [!code-cpp[wrl-logger-makeandinitialize#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Microsoft::WRL::Make](../windows/make-function.md)   
 [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)