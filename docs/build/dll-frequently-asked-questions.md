---
title: Preguntas más frecuentes sobre archivos DLL de MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a68a0ae6392c2a9a64c9ff6c567451c2672c861
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890197"
---
# <a name="dll-frequently-asked-questions"></a>Preguntas más frecuentes sobre archivos DLL

Siguientes son algunas de las preguntas más frecuentes (P+F) sobre los archivos DLL.

- [¿Puede crear una DLL de MFC de varios subprocesos?](#mfc_multithreaded_1)

- [¿Puede una aplicación multiproceso tener acceso a una DLL de MFC en distintos subprocesos?](#mfc_multithreaded_2)

- [¿Existen clases MFC o funciones que no se puede usar en una DLL de MFC?](#mfc_prohibited_classes)

- [¿Qué técnicas de optimización debo usar para mejorar el rendimiento de la aplicación cliente al cargar?](#mfc_optimization)

- [Hay una pérdida de memoria en mi DLL de MFC estándar, pero mi código se ve bien. ¿Cómo se puede encontrar la pérdida de memoria?](#memory_leak)

## <a name="mfc_multithreaded_1"></a> ¿Puede crear una DLL de MFC de varios subprocesos?

Excepto durante la inicialización, una DLL de MFC puede crear de forma segura varios subprocesos siempre y cuando utiliza el subproceso de Win32, como funciones de almacenamiento local (TLS) **TlsAlloc** para asignar el almacenamiento local de subproceso. Sin embargo, si utiliza una DLL de MFC **__declspec (Thread)** para asignar el almacenamiento local de subprocesos, la aplicación cliente debe vincularse implícitamente a la DLL. Si la aplicación cliente se vincula explícitamente a la DLL, la llamada a **LoadLibrary** no podrá cargar el archivo DLL. Para obtener más información acerca de las variables locales del subproceso en archivos DLL, consulte [subproceso](../cpp/thread.md).

Una DLL de MFC que crea un nuevo subproceso MFC durante el inicio dejará de responder cuando se cargue por una aplicación. Esto incluye cada vez que se crea un subproceso mediante una llamada a `AfxBeginThread` o `CWinThread::CreateThread` dentro:

- El `InitInstance` de un `CWinApp`-objeto derivado de un archivo DLL MFC.

- Un proporcionado `DllMain` o **RawDllMain** función en un archivo DLL MFC.

- Un proporcionado `DllMain` o **RawDllMain** función en un archivo DLL de extensión MFC.

## <a name="mfc_multithreaded_2"></a> ¿Puede una aplicación multiproceso tener acceso a una DLL de MFC en distintos subprocesos?

Aplicaciones multiproceso con comportamiento pueden tener acceso a archivos DLL de MFC estándar vinculados dinámicamente a MFC y archivos DLL de extensión MFC desde subprocesos diferentes. Y, a partir de Visual C++ versión 4.2, una aplicación puede tener acceso a archivos DLL de MFC estándar vinculados estáticamente a MFC desde varios subprocesos que se crean en la aplicación.

Antes de la versión 4.2, sólo un subproceso externo puede adjuntar a una DLL de MFC regulares que están vinculados estáticamente a MFC.

Tenga en cuenta que el término USRDLL ya no se usa en la documentación de Visual C++. DLL MFC estándar que se vincula estáticamente a MFC tiene las mismas características que el archivo USRDLL anterior.

## <a name="mfc_prohibited_classes"></a> ¿Existen clases MFC o funciones que no se puede usar en una DLL de MFC?

Uso de archivos DLL de extensión el `CWinApp`-clase derivada de la aplicación cliente. No deben tener su propio `CWinApp`-clase derivada.

Archivos DLL de MFC estándar debe tener un `CWinApp`-derivados de clase y un único objeto de esa clase de aplicación, como una aplicación MFC. A diferencia de la `CWinApp` objeto de una aplicación, el `CWinApp` objeto del archivo DLL no tiene un bombeo de mensajes principal.

Tenga en cuenta que dado que el `CWinApp::Run` mecanismo no se aplica a un archivo DLL, la aplicación es propietaria del suministro de mensajes principal. Si el archivo DLL abre los cuadros de diálogo no modal o tiene una ventana de marco principal de su propio, el bombeo de mensajes principal de la aplicación debe llamar a una rutina exportada por el archivo DLL, que a su vez llama a la `CWinApp::PreTranslateMessage` la función miembro de la DLL objeto de aplicación.

## <a name="mfc_optimization"></a> ¿Qué técnicas de optimización debo usar para mejorar la aplicación cliente&#39;rendimiento de s cuando se carga?

Si el archivo DLL es una DLL de MFC normal que se vincula estáticamente a MFC, cambiar a normal DLL de MFC que se vincule dinámicamente a MFC reduce el tamaño del archivo.

Si el archivo DLL tiene un gran número de funciones exportadas, utilice un archivo .def para exportar las funciones (en lugar de usar **__declspec (dllexport)**) y usar el archivo .def [NONAME (atributo)](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) en cada función exportada. El atributo NONAME hace que solo el valor ordinal y no el nombre de función que se almacenará en la tabla de exportación del archivo DLL, lo que reduce el tamaño del archivo.

Archivos DLL que se vinculan implícitamente a una aplicación se cargan cuando se cargue la aplicación. Para mejorar el rendimiento cuando se carga, intente dividir el archivo DLL en varias DLL diferentes. Coloque todas las funciones que necesite la aplicación que realiza la llamada inmediatamente después de la carga en un archivo DLL y la aplicación que realiza la llamada vincularse implícitamente a ese archivo DLL. Poner las demás funciones que la aplicación que realiza la llamada no necesita de inmediato en otro archivo DLL y vincule explícitamente la aplicación a ese archivo DLL. Para obtener más información, consulte [determinar qué método de vinculación para usar](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).

## <a name="memory_leak"></a> Hay&#39;s pérdidas de memoria en mi DLL de MFC normal, pero mi código se ve bien. ¿Cómo se puede encontrar la pérdida de memoria?

Una posible causa de la pérdida de memoria es que MFC crea objetos temporales que se utilizan dentro de las funciones de controlador de mensaje. En las aplicaciones MFC, estos objetos temporales se limpian automáticamente en el `CWinApp::OnIdle()` función que se llama entre el procesamiento de mensajes. Sin embargo, en las bibliotecas de vínculos dinámicos MFC (DLL), el `OnIdle()` función no se llama automáticamente. Como resultado, los objetos temporales no se limpian automáticamente una. Para limpiar los objetos temporales, debe llamar explícitamente el archivo DLL `OnIdle(1)` periódicamente.

## <a name="see-also"></a>Vea también

[Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)