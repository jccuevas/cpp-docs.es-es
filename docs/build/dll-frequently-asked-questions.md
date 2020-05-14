---
title: Preguntas más frecuentes sobre archivos DLL de MFC
ms.date: 05/06/2019
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 9108aaf3fcface847b0391455a2aecd4d45658c4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422827"
---
# <a name="dll-frequently-asked-questions"></a>Preguntas más frecuentes sobre archivos DLL

A continuación se incluyen algunas preguntas frecuentes sobre archivos DLL.

- [¿Puede un archivo DLL de MFC crear varios subprocesos?](#mfc_multithreaded_1)

- [¿Puede una aplicación multiproceso acceder a un archivo DLL de MFC en distintos subprocesos?](#mfc_multithreaded_2)

- [¿Hay clases o funciones de MFC que no se puedan usar en un archivo DLL de MFC?](#mfc_prohibited_classes)

- [¿Qué técnicas de optimización se deben usar para mejorar el rendimiento de las aplicaciones cliente al cargarlas?](#mfc_optimization)

- [Hay una pérdida de memoria en el archivo DLL de MFC estándar, pero no encuentro el problema en el código. ¿Cómo se puede localizar la pérdida de memoria?](#memory_leak)

## <a name="can-an-mfc-dll-create-multiple-threads"></a><a name="mfc_multithreaded_1"></a> ¿Puede un archivo DLL de MFC crear varios subprocesos?

Excepto durante la inicialización, un archivo DLL de MFC puede crear varios subprocesos de forma segura, siempre y cuando use las funciones de almacenamiento local para el subproceso (TLS) de Win32, como **TlsAlloc**, para asignar dicho almacenamiento. Aun así, si un archivo DLL de MFC usa **__declspec(thread)** para asignar el almacenamiento local para el subproceso, la aplicación cliente debe estar vinculada implícitamente al archivo DLL. Si la aplicación cliente se vincula explícitamente al archivo DLL, la llamada a **LoadLibrary** no cargará correctamente el archivo DLL. Para obtener más información sobre las variables locales de subproceso en archivos DLL, vea [thread](../cpp/thread.md).

Un archivo DLL de MFC que cree un subproceso de MFC durante el inicio dejará de responder cuando una aplicación lo cargue. Esto incluye los casos en los que se crea un subproceso mediante una llamada a `AfxBeginThread` o `CWinThread::CreateThread` dentro de:

- La instancia `InitInstance` de un objeto derivado de `CWinApp`en un archivo DLL de MFC estándar.

- Una función`DllMain` o **RawDllMain** proporcionada en un archivo DLL de MFC estándar.

- Una función`DllMain` o **RawDllMain** proporcionada en un archivo DLL de extensión de MFC.

## <a name="can-a-multithreaded-application-access-an-mfc-dll-in-different-threads"></a><a name="mfc_multithreaded_2"></a> ¿Puede una aplicación multiproceso acceder a un archivo DLL de MFC en distintos subprocesos?

Las aplicaciones multiproceso pueden acceder a archivos DLL de MFC estándar que se vinculan dinámicamente a MFC y a archivos DLL de extensión de MFC desde distintos subprocesos. Una aplicación puede acceder a archivos DLL de MFC estándar que se vinculan estáticamente a MFC desde varios subprocesos creados en la aplicación.

## <a name="are-there-any-mfc-classes-or-functions-that-cannot-be-used-in-an-mfc-dll"></a><a name="mfc_prohibited_classes"></a> ¿Hay clases o funciones de MFC que no se puedan usar en un archivo DLL de MFC?

Los archivos DLL de extensión usan la clase derivada de `CWinApp` de la aplicación cliente. No deben tener su propia clase derivada de `CWinApp`.

Los archivos DLL de MFC estándar deben tener una clase derivada de `CWinApp` y un solo objeto de esa clase de aplicación, igual que una aplicación MFC. A diferencia del objeto `CWinApp` de una aplicación, el objeto `CWinApp` del archivo DLL no tiene un suministro de mensajes principal.

Tenga en cuenta que, dado que el mecanismo `CWinApp::Run` no se aplica a un archivo DLL, la aplicación posee el suministro de mensajes principal. Si el archivo DLL abre cuadros de diálogo no modales o tiene una ventana de marco principal propia, el suministro de mensajes principal de la aplicación debe llamar a una rutina exportada por el archivo DLL, que a su vez llama a la función miembro `CWinApp::PreTranslateMessage` del objeto de aplicación del archivo DLL.

## <a name="what-optimization-techniques-should-i-use-to-improve-the-client-application39s-performance-when-loading"></a><a name="mfc_optimization"></a> ¿Qué técnicas de optimización se deben usar para mejorar el rendimiento de las aplicaciones cliente al cargarlas?

Si el archivo DLL es un archivo DLL de MFC estándar que se vincula estáticamente a MFC, cuando se cambia a uno vinculado dinámicamente a MFC, se reduce el tamaño del archivo.

Si el archivo DLL tiene un gran número de funciones exportadas, use un archivo .def para exportar las funciones (en lugar de **__declspec(dllexport)** ) y use el archivo .def [NONAME attribute](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) en cada función exportada. El atributo NONAME hace que solo el valor ordinal, y no el nombre de función, se almacene en la tabla de exportación del archivo DLL, lo que reduce el tamaño del archivo.

Los archivos DLL que están vinculados implícitamente a una aplicación se cargan cuando se carga la aplicación. Para mejorar el rendimiento de la carga, intente dividir el archivo DLL en varios archivos de este tipo. Coloque todas las funciones que la aplicación que realiza la llamada necesita justo después de cargarse en un archivo DLL y haga que la aplicación que realiza la llamada se vincule implícitamente a ese archivo DLL. Coloque las demás funciones que la aplicación que realiza la llamada no necesita de inmediato en otro archivo DLL y haga que la aplicación se vincule explícitamente a ese archivo DLL. Para obtener más información, vea [Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).

## <a name="there39s-a-memory-leak-in-my-regular-mfc-dll-but-my-code-looks-fine-how-can-i-find-the-memory-leak"></a><a name="memory_leak"></a> Hay una pérdida de memoria en el archivo DLL de MFC estándar, pero no encuentro el problema en el código. ¿Cómo se puede localizar la pérdida de memoria?

Una posible causa de la pérdida de memoria es que MFC crea objetos temporales que se usan en funciones del controlador de mensajes. En las aplicaciones MFC, estos objetos temporales se limpian automáticamente en la función `CWinApp::OnIdle()` a la que se llama entre el procesamiento de mensajes. Aun así, en las bibliotecas de vínculos dinámicos (DLL) de MFC, no se llama automáticamente a la función `OnIdle()`. Como resultado, los objetos temporales no se limpian automáticamente. Para limpiar los objetos temporales, el archivo DLL debe llamar explícitamente a `OnIdle(1)` de forma periódica.

## <a name="see-also"></a>Vea también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
