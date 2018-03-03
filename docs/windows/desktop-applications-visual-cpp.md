---
title: Aplicaciones de escritorio (Visual C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7e2da53a234f63bfd4c8a7f84ec5c107426f0e7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="desktop-applications-visual-c"></a>Aplicaciones de escritorio (Visual C++)
A *aplicación de escritorio* en C++ es una aplicación nativa que se puede acceder al conjunto completo de API de Windows y ambos se ejecuta en una ventana o en la consola del sistema. Aplicaciones de escritorio de C++ pueden ejecutar en Windows XP y Windows 10 (Aunque oficialmente no se admite Windows XP y hay muchas de las API de Windows que se han introducido desde ese momento).   Una aplicación de escritorio es distinta de una aplicación de plataforma Universal de Windows (UWP), que se puede ejecutar en equipos que ejecutan Windows 10 y también en XBox, Windows Phone, Surface Hub y otros dispositivos. Para obtener más información acerca de vs de escritorio. Las aplicaciones de UWP, vea [elegir la tecnología](https://msdn.microsoft.com/en-us/library/windows/desktop/dn614993\(v=vs.85\).aspx).  
  
 **Terminología**  
  
-   A *Win32* aplicación es una aplicación de escritorio de C++ que pueden hacer uso de nativo de Windows [las API de C de Windows o COM APIs](https://msdn.microsoft.com/en-us/library/windows/desktop/ff818516\(v=vs.85\).aspx) CRT y las API de biblioteca estándar y 3rd bibliotecas de entidad. Una aplicación de Win32 que se ejecuta en una ventana exige al programador que funciona de forma explícita con los mensajes de Windows dentro de una función de procedimiento de Windows. A pesar del nombre, una aplicación de Win32 puede compilarse como una (x86) 32 bits o 64 bits (x64) binario. En el IDE de Visual Studio, los términos x86 y Win32 son sinónimos.  
  
-   El [modelo de objetos componentes (COM)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms694363\(v=vs.85\).aspx) es una especificación que permite a los programas escritos en lenguajes diferentes se comuniquen entre sí. La interfaz de Windows muchos componentes se implementan como objetos COM y siguen las reglas COM estándar para la creación de objetos, la destrucción de detección y el objeto.  Usar objetos COM desde aplicaciones de escritorio de C++ es relativamente sencillo, pero escribir su propio objeto COM es más avanzado. El [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) proporciona macros y funciones auxiliares que simplifican el desarrollo de COM.  
  
-   Una aplicación MFC es una aplicación de escritorio de Windows que usan la [Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md) para crear la interfaz de usuario. Una aplicación MFC también puede utilizar los componentes COM, así como CRT y las API de biblioteca estándar. MFC proporciona un contenedor fino de C++ orientado a objetos con respecto a las API de Windows y el bucle de mensajes de ventana. MFC es la opción predeterminada para las aplicaciones, especialmente las aplicaciones de tipo empresarial, que tienen una gran cantidad de controles de interfaz de usuario o controles de usuario personalizados. MFC proporciona clases auxiliares útiles para la administración de ventanas, serialización, manipulación de texto, impresión y elementos de la interfaz de usuario moderna, como la cinta de opciones. Para que sea eficaz con MFC debe estar familiarizado con Win32.  
  
-   C++ / CLI aplicación o un componente usa extensiones a la sintaxis de C++ (según lo permitido por la especificación de C++) para habilitar la interacción entre .NET y código de C/C ++ nativo.  C++ / CLI aplicación puede tener elementos que se ejecutan de forma nativa y elementos que se ejecutan en .NET Framework con acceso a la biblioteca de clases de Base. NET. C++ / CLI es la opción preferida cuando haya código C++ nativo que necesita para trabajar con código escrito en C# o Visual Basic. Sirve principalmente para su uso en archivos DLL de .NET en lugar de en el código de la interfaz de usuario. Para obtener más información, consulte [programación de .NET con C++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
 Puede usar cualquier aplicación de escritorio de C++ en tiempo de ejecución de C (CRT) y la biblioteca estándar de las clases y funciones, objetos COM y las funciones de Windows públicas, que se conocen colectivamente como la API de Windows. Para ver una introducción a las aplicaciones de escritorio de Windows en C++, consulte [Cómo aprender a programar para Windows en C++](http://go.microsoft.com/fwlink/p/?LinkId=262281).  
  
## <a name="in-this-section"></a>En esta sección  
  
|Title|Descripción|  
|-----------|-----------------|  
|[Aplicaciones de consola](../windows/console-applications-in-visual-cpp.md)|Contiene información acerca de las aplicaciones de consola. Una aplicación de consola Win32 (o Win64) no tiene ninguna ventana propia ni ningún bucle de mensajes. Se ejecuta en la ventana de la consola; la entrada y la salida se controlan a través de la línea de comandos.|  
|[Aplicaciones de escritorio de Windows](../windows/windows-desktop-applications-cpp.md)|Cómo crear aplicaciones de escritorio que se ejecutan en windows en lugar de la consola.|  
|[Recursos para crear un juego usando DirectX (C++)](../windows/resources-for-creating-a-game-using-directx.md)|Vínculos a contenido para crear juegos en C++.|  
|[Tutorial: Crear y utilizar una biblioteca estática](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Cómo crear un archivo binario .lib.|  
|[Procedimiento para usar el SDK de Windows 10 en una aplicación de escritorio de Windows](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Indica los pasos necesarios para configurar el proyecto de desarrollo con el SDK de Windows 10.|  
  
## <a name="related-articles"></a>Artículos relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Desarrollo de Windows](http://go.microsoft.com/fwlink/p/?LinkId=262282)|Contiene información sobre la API de Windows y COM. (Algunas API de Windows y archivos DLL de terceros se implementan como objetos COM).|  
|[Hilo: desarrollo de aplicaciones en C++ para Windows 7](http://go.microsoft.com/fwlink/p/?LinkId=262284)|Describe cómo crear una aplicación de escritorio de Windows de cliente que use animaciones de Windows y Direct2D para crear una interfaz de usuario basada en carrusel.  Este tutorial no se ha actualizado desde Windows 7, pero sigue ofreciendo una introducción de throough a la programación de Win32.|  
|[Visual C++](../visual-cpp-in-visual-studio.md)|Describe las principales características de Visual C++ en Visual Studio y vínculos al resto de la documentación sobre Visual C++.|  
  
## <a name="see-also"></a>Vea también  
 [Visual C++](../visual-cpp-in-visual-studio.md)
