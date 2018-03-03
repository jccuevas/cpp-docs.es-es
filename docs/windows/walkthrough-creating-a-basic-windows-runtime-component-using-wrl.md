---
title: "Tutorial: Crear un componente de tiempo de ejecución básico de Windows mediante WRL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 6e3f0986-7905-4f94-90e5-22c2ebfc8cd0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5859f3ebfcb55427e239a0018d539e2f4df13800
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-creating-a-basic-windows-runtime-component-using-wrl"></a>Tutorial: Crear un componente básico de Windows Runtime mediante WRL
Este documento muestra cómo usar la biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución para crear un componente básico de Windows en tiempo de ejecución. El componente agrega dos números y genera un evento cuando el resultado es primo. Este documento también muestra cómo utilizar el componente de una aplicación de plataforma Universal de Windows que usa JavaScript.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   Experiencia con el [en tiempo de ejecución de Windows](http://msdn.microsoft.com/library/windows/apps/br211377.aspx).  
  
-   Experiencia con COM.  
  
### <a name="to-create-a-basic-windows-runtime-component-that-adds-two-numbers"></a>Para crear un componente básico de Windows Runtime que suma dos números  
  
1.  En Visual Studio, cree un Visual C++ `WRLClassLibrary` proyecto. El documento [plantilla de proyecto de biblioteca de clases](../windows/wrl-class-library-project-template.md) describe cómo descargar esta plantilla. Dé un nombre al proyecto `Contoso`.  
  
2.  En Contoso.cpp y Contoso.idl, reemplace todas las instancias de "WinRTClass" con "Calculadora".  
  
3.  En Contoso.idl, agregue el `Add` método para el `ICalculator` interfaz.  
  
     [!code-cpp[wrl-basic-component#1](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_1.idl)]  
  
4.  En Contoso.cpp, agregue el `Add` método a la `public` sección de la `Calculator` clase.  
  
     [!code-cpp[wrl-basic-component#2](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_2.cpp)]  
  
    > [!IMPORTANT]
    >  Dado que va a crear un componente COM, recuerde que debe usar el `__stdcall` convención de llamada.  
  
     Se recomienda que use `_Out_` y otras anotaciones de lenguaje (SAL) de anotación de origen para describir la forma en que una función usa sus parámetros. Las anotaciones de SAL también describen valores devueltos. Las anotaciones de SAL funcionan con el [herramienta de análisis de código de C/C ++](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) para detectar posibles defectos en C y C++ el código fuente. Errores de codificación más comunes que se notifican mediante la herramienta, destacan las saturaciones de búfer, memoria sin inicializar, desreferenciación del puntero null y pérdidas de memoria y los recursos.  
  
### <a name="to-use-the-component-from-a-universal-windows-platform-app-that-uses-javascript"></a>Para usar el componente de una aplicación de plataforma Universal de Windows usa JavaScript  
  
1.  En Visual Studio, agregue un nuevo JavaScript `Blank App` proyecto a la `Contoso` solución. Dé un nombre al proyecto `CalculatorJS`.  
  
2.  En el `CalculatorJS` del proyecto, agregue una referencia a la `Contoso` proyecto.  
  
3.  En default.html, reemplaza el `body` sección con estos elementos de interfaz de usuario:  
  
     [!code-html[wrl-basic-component#3](../windows/codesnippet/Html/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_3.html)]  
  
4.  En el archivo default.js, implementar la `OnClick` función.  
  
     [!code-javascript[wrl-basic-component#4](../windows/codesnippet/JavaScript/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_4.js)]  
  
    > [!NOTE]
    >  En JavaScript, la primera letra de un nombre de método se cambia a minúscula para que coincida con las convenciones de nomenclatura estándares.  
  
### <a name="to-add-an-event-that-fires-when-a-prime-number-is-calculated"></a>Para agregar un evento que se desencadena cuando se calcula un número primo  
  
1.  En Contoso.idl, antes de la declaración de `ICalculator`, defina el tipo de delegado, `PrimeNumberEvent`, lo que proporciona un `int` argumento.  
  
     [!code-cpp[wrl-basic-component#5](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_5.idl)]  
  
     Cuando se usa el `delegate` palabra clave, el compilador MIDL crea una interfaz que contiene un `Invoke` método que coincide con la firma de delegado. En este ejemplo, el archivo generado Contoso_h.h define la `IPrimeNumberEvent` interfaz, que se usa más adelante en este procedimiento.  
  
     [!code-cpp[wrl-basic-component#13](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_6.cpp)]  
  
2.  En el `ICalculator` interfaz, defina el `PrimeNumberFound` eventos. El `eventadd` y `eventremove` atributos especifican que el consumidor de la `ICalculator` interfaz puede suscribirse a y cancelar la suscripción a este evento.  
  
     [!code-cpp[wrl-basic-component#6](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_7.idl)]  
  
3.  En Contoso.cpp, agregue un `private` [Microsoft::WRL::EventSource](../windows/eventsource-class.md) variable miembro para administrar los suscriptores de eventos e invocar el controlador de eventos.  
  
     [!code-cpp[wrl-basic-component#7](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_8.cpp)]  
  
4.  En Contoso.cpp, implemente el `add_PrimeNumberFound` y `remove_PrimeNumberFound` métodos.  
  
     [!code-cpp[wrl-basic-component#8](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_9.cpp)]  
  
### <a name="to-raise-the-event-when-a-prime-number-is-calculated"></a>Para generar el evento cuando se calcula un número primo  
  
1.  En Contoso.cpp, agregue el `IsPrime` método a la `private` sección de la `Calculator` clase.  
  
     [!code-cpp[wrl-basic-component#12](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_10.cpp)]  
  
2.  Modificar el `Calculator`del `Add` método para llamar a la [Microsoft::WRL::EventSource::InvokeAll](../windows/eventsource-invokeall-method.md) método cuando se calcula un número primo.  
  
     [!code-cpp[wrl-basic-component#11](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_11.cpp)]  
  
### <a name="to-handle-the-event-from-javascript"></a>Al controlar el evento de JavaScript  
  
1.  En default.html, modifique la `body` sección debe incluir un área de texto que contiene números primos.  
  
     [!code-html[wrl-basic-component#9](../windows/codesnippet/Html/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_12.html)]  
  
2.  En default.js, modifique la `Add` función para controlar la `PrimeNumberFound` eventos. El controlador de eventos, anexa el número primo hasta el área de texto que se definió en el paso anterior.  
  
     [!code-javascript[wrl-basic-component#10](../windows/codesnippet/JavaScript/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_13.js)]  
  
    > [!NOTE]
    >  En JavaScript, los nombres de eventos se cambian a minúsculas y van precedidos de "on" para que coincida con las convenciones de nomenclatura estándares.  
  
 En la siguiente ilustración muestra la aplicación de calculadora básica.  
  
 ![Aplicación de calculadora básica con JavaScript](../windows/media/wrl_basic_component.png "WRL_Basic_Component")  
  
## <a name="next-steps"></a>Pasos siguientes  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Plantilla de proyecto de biblioteca de clases](../windows/wrl-class-library-project-template.md)   
 [Herramienta de análisis de código de C/C ++](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)