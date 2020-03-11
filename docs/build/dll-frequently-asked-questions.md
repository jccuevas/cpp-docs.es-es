---
title: Preguntas más frecuentes sobre archivos DLL de MFC
ms.date: 05/06/2019
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 9108aaf3fcface847b0391455a2aecd4d45658c4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856955"
---
# <a name="dll-frequently-asked-questions"></a>Preguntas más frecuentes sobre archivos DLL

A continuación se muestran algunas de las preguntas más frecuentes (p + f) sobre los archivos dll.

- [¿Puede un archivo DLL de MFC crear varios subprocesos?](#mfc_multithreaded_1)

- [¿Puede una aplicación multiproceso tener acceso a un archivo DLL de MFC en diferentes subprocesos?](#mfc_multithreaded_2)

- [¿Hay alguna clase o función MFC que no se pueda usar en un archivo DLL de MFC?](#mfc_prohibited_classes)

- [¿Qué técnicas de optimización debo usar para mejorar el rendimiento de la aplicación cliente al cargar?](#mfc_optimization)

- [Hay una fuga de memoria en el archivo DLL de MFC normal, pero mi código es correcto. ¿Cómo puedo encontrar la fuga de memoria?](#memory_leak)

## <a name="mfc_multithreaded_1"></a>¿Puede un archivo DLL de MFC crear varios subprocesos?

Excepto durante la inicialización, un archivo DLL de MFC puede crear de forma segura varios subprocesos siempre y cuando use las funciones de almacenamiento local de subprocesos (TLS) de Win32 como **TlsAlloc** para asignar el almacenamiento local de subprocesos. Sin embargo, si un archivo DLL de MFC utiliza **__declspec (subproceso)** para asignar el almacenamiento local de subprocesos, la aplicación cliente debe estar vinculada implícitamente al archivo dll. Si la aplicación cliente se vincula explícitamente al archivo DLL, la llamada a **LoadLibrary** no cargará correctamente el archivo dll. Para obtener más información sobre las variables locales de subproceso en archivos dll, vea [Thread](../cpp/thread.md).

Un archivo DLL de MFC que crea un nuevo subproceso MFC durante el inicio dejará de responder cuando una aplicación lo cargue. Esto incluye siempre que se crea un subproceso llamando a `AfxBeginThread` o `CWinThread::CreateThread` dentro de:

- `InitInstance` de un objeto derivado de `CWinApp`en un archivo DLL de MFC normal.

- Una función `DllMain` o **RawDllMain** proporcionada en un archivo dll de MFC normal.

- Una función `DllMain` o **RawDllMain** proporcionada en un archivo dll de extensión de MFC.

## <a name="mfc_multithreaded_2"></a>¿Puede una aplicación multiproceso tener acceso a un archivo DLL de MFC en diferentes subprocesos?

Las aplicaciones multiproceso pueden tener acceso a los archivos dll de MFC estándar que se vinculan dinámicamente a los archivos dll de extensión MFC y MFC desde distintos subprocesos. Una aplicación puede tener acceso a archivos dll de MFC normales que se vinculan estáticamente a MFC desde varios subprocesos creados en la aplicación.

## <a name="mfc_prohibited_classes"></a>¿Hay alguna clase o función MFC que no se pueda usar en un archivo DLL de MFC?

Los archivos dll de extensión utilizan la clase derivada de `CWinApp`de la aplicación cliente. No deben tener su propia clase derivada de `CWinApp`.

Los archivos dll de MFC normales deben tener una clase derivada de `CWinApp`y un único objeto de esa clase de aplicación, al igual que una aplicación MFC. A diferencia del objeto de `CWinApp` de una aplicación, el objeto `CWinApp` de la DLL no tiene un suministro de mensajes principal.

Tenga en cuenta que, dado que el mecanismo de `CWinApp::Run` no se aplica a un archivo DLL, la aplicación posee el suministro de mensajes principal. Si el archivo DLL abre cuadros de diálogo no modales o tiene una ventana de marco principal propia, el suministro de mensajes principal de la aplicación debe llamar a una rutina exportada por el archivo DLL, que a su vez llama a la función miembro `CWinApp::PreTranslateMessage` del objeto de aplicación del archivo DLL.

## <a name="mfc_optimization"></a>¿Qué técnicas de optimización debo usar para mejorar el rendimiento&#39;de las aplicaciones cliente al cargar?

Si el archivo DLL es un archivo DLL de MFC normal que se vincula estáticamente a MFC, al cambiarlo a un archivo DLL de MFC normal que está vinculado dinámicamente a MFC se reduce el tamaño del archivo.

Si el archivo DLL tiene un gran número de funciones exportadas, utilice un archivo. def para exportar las funciones (en lugar de utilizar **__declspec (dllexport)** ) y use el [atributo Noname](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) del archivo. def en cada función exportada. El atributo Noname solo hace que el valor ordinal y no el nombre de función se almacenen en la tabla de exportación del archivo DLL, lo que reduce el tamaño del archivo.

Los archivos DLL que están vinculados implícitamente a una aplicación se cargan cuando se carga la aplicación. Para mejorar el rendimiento al cargar, intente dividir el archivo DLL en diferentes dll. Coloque todas las funciones que la aplicación que realiza la llamada necesita inmediatamente después de cargarse en un archivo DLL y hacer que la aplicación que realiza la llamada se vincule implícitamente a ese archivo DLL. Coloque las demás funciones que la aplicación que realiza la llamada no necesita de inmediato en otro archivo DLL y que la aplicación se vincula explícitamente a esa DLL. Para obtener más información, vea [vincular un ejecutable a un archivo dll](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).

## <a name="memory_leak"></a>Se&#39;ha producido una fuga de memoria en el archivo dll de MFC normal, pero el código es correcto. ¿Cómo puedo encontrar la fuga de memoria?

Una posible causa de la pérdida de memoria es que MFC crea objetos temporales que se utilizan en las funciones del controlador de mensajes. En las aplicaciones MFC, estos objetos temporales se limpian automáticamente en la función `CWinApp::OnIdle()` a la que se llama entre el procesamiento de mensajes. Sin embargo, en las bibliotecas de vínculos dinámicos (dll) de MFC, no se llama automáticamente a la función `OnIdle()`. Como resultado, los objetos temporales no se limpian automáticamente. Para limpiar los objetos temporales, el archivo DLL debe llamar explícitamente a `OnIdle(1)` de forma periódica.

## <a name="see-also"></a>Consulte también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
