---
title: "Aplicaciones de escritorio de Windows (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
caps.latest.revision: 17
caps.handback.revision: 12
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Aplicaciones de escritorio de Windows (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede crear una aplicación de escritorio de Windows cuando desee crear una aplicación de escritorio nativa que tenga una interfaz de usuario basada en la ventanas y se pueda ejecutar en versiones de Windows de Windows XP a Windows 10 en el escritorio de Windows.  
  
 Un *aplicación de escritorio de Windows* \(a veces denominada aplicación de Win32 en la literatura anterior\) es el término convencional para una aplicación que usa bucles de mensajes para controlar los mensajes de Windows directamente en lugar de usar un marco como Microsoft Foundation Classes \(MFC\), Active Template Library \(ATL\) o .NET Framework. Una aplicación de escritorio de Windows en C\+\+ puede usar el runtime de C \(CRT\), las clases y las funciones de la Biblioteca de plantillas estándar \(STL\), los objetos COM y cualquiera de las funciones de Windows públicas, que se conocen colectivamente como la API de Windows. Para ver una introducción a las aplicaciones de escritorio de Windows en C\+\+, consulte [Cómo aprender a programar para Windows en C\+\+](http://go.microsoft.com/fwlink/p/?LinkId=262281).  
  
 Una aplicación de escritorio de Windows es una forma de crear una aplicación de escritorio nativa para Windows; la otra forma es una aplicación de Microsoft Foundation Classes. MFC es la opción predeterminada para las aplicaciones, en especial las aplicaciones de tipo empresarial, que tienen muchos controles de interfaz de usuario o controles de usuario personalizados. MFC proporciona clases auxiliares útiles para la serialización, la manipulación de texto, la impresión y elementos modernos de la interfaz de usuario tales como la cinta de opciones. Estas clases no están disponibles para aplicaciones de escritorio de Windows.  
  
## Artículos relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Desarrollo de Windows](http://go.microsoft.com/fwlink/p/?LinkId=262282)|Contiene información sobre la API de Windows y COM. \(Algunas API de Windows y archivos DLL de terceros se implementan como objetos COM\).|  
|[Hilo: desarrollo de aplicaciones en C\+\+ para Windows 7](http://go.microsoft.com/fwlink/p/?LinkId=262284)|Describe cómo crear una aplicación de escritorio de Windows de cliente que use animaciones de Windows y Direct2D para crear una interfaz de usuario basada en carrusel.|  
|[Aplicaciones de consola](../Topic/Console%20Applications%20in%20Visual%20C++.md)|Contiene información acerca de las aplicaciones de consola. Una aplicación de consola Win32 \(o Win64\) no tiene ninguna ventana propia ni ningún bucle de mensajes. Se ejecuta en la ventana de la consola; la entrada y la salida se controlan a través de la línea de comandos.|  
|[Visual C\+\+](../top/visual-cpp-in-visual-studio-2015.md)|Describe las principales características de Visual C\+\+ en Visual Studio y vínculos al resto de la documentación sobre Visual C\+\+.|  
|[Centro para desarrolladores de Visual C\+\+](http://go.microsoft.com/fwlink/p/?LinkId=252885) en el sitio web de MSDN|Contiene los tutoriales, las entradas de blog y los artículos que son pertinentes para las aplicaciones de escritorio de Windows.|  
|[Procedimiento de uso del SDK de Windows 10 en una aplicación de escritorio de Windows](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Indica los pasos necesarios para configurar el proyecto de desarrollo con el SDK de Windows 10.|