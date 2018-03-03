---
title: "Preguntas más frecuentes sobre archivos DLL de MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 39c3a36f697527c7e133409f49656e4415f86a7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dll-frequently-asked-questions"></a>Preguntas más frecuentes sobre archivos DLL  
  
Estas son algunas de las preguntas frecuentes (P+F) sobre los archivos DLL.  
    
-   [¿Puede una DLL de MFC crear varios subprocesos?](#mfc_multithreaded_1)  

-   [¿Puede una aplicación multiproceso tener acceso a una DLL de MFC en distintos subprocesos?](#mfc_multithreaded_2)  
  
-   [¿Existen las clases o funciones MFC que no se puede usar en una DLL de MFC?](#mfc_prohibited_classes)  
  
-   [¿Qué técnicas de optimización debo usar para mejorar el rendimiento de la aplicación cliente al cargarlas?](#mfc_optimization)  
  
-   [Hay una pérdida de memoria en mi DLL de MFC estándar, pero mi código muestre correctamente. ¿Cómo se puede averiguar la fuga de memoria?](#memory_leak)  

## <a name="mfc_multithreaded_1"></a>¿Puede una DLL de MFC crear varios subprocesos?  
  
Salvo durante la inicialización, una DLL de MFC puede crear de forma segura varios subprocesos siempre y cuando utiliza el subproceso de Win32 funciones de almacenamiento local (TLS) como **TlsAlloc** para asignar el almacenamiento local de subproceso. Sin embargo, si utiliza una DLL de MFC **__declspec (Thread)** para asignar el almacenamiento local de subprocesos, la aplicación cliente debe vincularse implícitamente al archivo DLL. Si la aplicación cliente se vincula explícitamente al archivo DLL, la llamada a **LoadLibrary** no cargará correctamente el archivo DLL. Para obtener más información acerca de cómo crear varios subprocesos dentro de archivos DLL de MFC, vea el artículo de Knowledge Base "PRB: al llamar a LoadLibrary() to carga una DLL que tiene Static TLS" (Q118816). Para obtener más información acerca de las variables locales del subproceso en archivos DLL, consulte [subproceso](../cpp/thread.md).
  
 Una DLL de MFC que crea un nuevo subproceso MFC durante el inicio dejará de responder cuando se cargue una aplicación. Esto incluye cada vez que se crea un subproceso mediante una llamada a `AfxBeginThread` o `CWinThread::CreateThread` en:  
  
-   El `InitInstance` de un `CWinApp`-objeto derivado de una DLL de MFC normal.  
  
-   Un proporcionado `DllMain` o **RawDllMain** función en una DLL de MFC estándar.  
  
-   Un proporcionado `DllMain` o **RawDllMain** función en un archivo DLL de extensión MFC.  
  
 Para obtener más información sobre la creación de subprocesos durante la inicialización, vea el artículo de Knowledge Base "PRB: no se puede crear un MFC Thread During DLL Startup" (Q142243).  
  
## <a name="mfc_multithreaded_2"></a>¿Puede una aplicación multiproceso tener acceso a una DLL de MFC en distintos subprocesos?
Aplicaciones multiproceso pueden tener acceso a archivos DLL de MFC estándar que se vinculen dinámicamente a MFC y archivos DLL de extensión MFC desde subprocesos diferentes. Y, a partir de Visual C++ versión 4.2, una aplicación puede tener acceso a los archivos DLL de MFC estándar vinculados estáticamente a MFC desde varios subprocesos creados en la aplicación.  
  
 Antes de la versión 4.2, solo un subproceso externo pudo asociar a una DLL de MFC normal que se vinculan estáticamente a MFC. Para obtener más información sobre las restricciones de acceso a archivos DLL de MFC estándar vinculados estáticamente a MFC desde varios subprocesos (antes de Visual C++ versión 4.2), vea el artículo de Knowledge Base, "varios subprocesos y MFC _USRDLL" (Q122676).  
  
 Tenga en cuenta que el término USRDLL ya no se usa en la documentación de Visual C++. Una DLL de MFC normal que se vincula estáticamente a MFC tiene las mismas características que el antiguo archivo USRDLL.  


## <a name="mfc_prohibited_classes"></a>¿Existen las clases o funciones MFC que no se puede usar en una DLL de MFC?
Uso de archivos DLL de extensión del `CWinApp`-clase derivada de la aplicación cliente. No deben tener sus propios `CWinApp`-clase derivada.  
  
archivos DLL de MFC estándar debe tener un `CWinApp`-derivados de clase y un único objeto de esa clase de aplicación, como sucede en una aplicación MFC. A diferencia de la `CWinApp` objeto de una aplicación, la `CWinApp` objeto de la DLL no tiene un suministro de mensajes principal.  
  
 Tenga en cuenta que, dado el `CWinApp::Run` mecanismo no se aplica a un archivo DLL, la aplicación es propietaria del suministro principal de mensajes. Si el archivo DLL abre cuadros de diálogo no modales o tiene una ventana de marco principal de su propia, el suministro de mensajes principal de la aplicación debe llamar a una rutina exportada por el archivo DLL, que a su vez llama a la `CWinApp::PreTranslateMessage` función miembro de objeto de aplicación de los archivos DLL.  

## <a name="mfc_optimization"></a>¿Qué técnicas de optimización debo utilizar para mejorar la aplicación cliente &#39; rendimiento de s cuando se carga?
Si el archivo DLL es una DLL de MFC normal que se vincula estáticamente a MFC, cambiar a normal DLL de MFC que se vincule dinámicamente a MFC reduce el tamaño del archivo.  
  
 Si el archivo DLL tiene un gran número de funciones exportadas, utilice un archivo .def para exportar las funciones (en lugar de usar **__declspec (dllexport)**) y usar el archivo .def [NONAME (atributo)](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) en cada función exportada. El atributo NONAME hace que solo el valor ordinal y no el nombre de función que se almacenará en la tabla de exportación del archivo DLL, lo que reduce el tamaño del archivo.  
  
 Archivos DLL que se vinculan implícitamente a una aplicación se cargan cuando se carga la aplicación. Para mejorar el rendimiento cuando se carga, intente dividir el archivo DLL en varias DLL diferentes. Coloque todas las funciones que necesite la aplicación que realiza la llamada inmediatamente después de la carga en un archivo DLL y la aplicación que realiza la llamada que se vincule implícitamente a ese archivo DLL. Poner las demás funciones que la aplicación que realiza la llamada no es necesario inmediatamente en el otro archivo DLL y vincule explícitamente la aplicación a ese archivo DLL. Para obtener más información, consulte [determinar qué método de vinculación para usar](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).  

## <a name="memory_leak"></a>Se &#39; s una fuga de memoria en mi regular DLL de MFC, pero el código parece bien. ¿Cómo se puede averiguar la fuga de memoria?  
  
Una posible causa de la pérdida de memoria es que MFC crea objetos temporales que se utilizan dentro de las funciones de controlador de mensaje. En las aplicaciones MFC, esos objetos temporales se limpian automáticamente en el `CWinApp::OnIdle()` función que se llama entre el procesamiento de mensajes. Sin embargo, en las bibliotecas de vínculos dinámicos MFC (DLL), el `OnIdle()` no se llama automáticamente a función. Como resultado, los objetos temporales no son limpia automáticamente. Para limpiar los objetos temporales, debe llamar explícitamente el archivo DLL `OnIdle(1)` periódicamente.  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)