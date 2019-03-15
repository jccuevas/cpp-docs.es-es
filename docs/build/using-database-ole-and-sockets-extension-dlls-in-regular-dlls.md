---
title: Uso de archivos DLL de extensión de base de datos, OLE y Sockets MFC en archivos DLL de MFC estándar
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
ms.openlocfilehash: d08822a04abe5a01883ad8aa1bd6d94269e810cc
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "57807980"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>Uso de archivos DLL de extensión de base de datos, OLE y Sockets MFC en archivos DLL de MFC estándar

Cuando se usa una extensión MFC DLL desde una DLL de MFC regular, si la extensión MFC DLL no está conectada a la **CDynLinkLibrary** objeto de cadena de la DLL de MFC regular, pueden surgir uno o más de un conjunto de problemas relacionados. Dado que admiten las versiones de depuración de la base de datos de MFC, OLE y Sockets archivos DLL se implementa como archivos DLL de extensión MFC, podría ver problemas similares si usa estos MFC características, incluso si no está explícitamente utilizando cualquiera de su propios archivos DLL de extensión MFC. Algunos síntomas son:

- Cuando intenta deserializar un objeto de un tipo de clase definido en la extensión MFC DLL, el mensaje "Advertencia: No se puede cargar CSuClase desde el archivo. Clase no definido". aparece en la ventana de depuración de seguimiento y el objeto no se puede serializar.

- Se podría producir una excepción que indica la clase incorrecto.

- No se pudo cargar porque los recursos almacenados en el archivo DLL de extensión MFC `AfxFindResourceHandle` devuelve **NULL** o un identificador de recursos incorrecto.

- `DllGetClassObject`, `DllCanUnloadNow`y el `UpdateRegistry`, `Revoke`, `RevokeAll`, y `RegisterAll` funciones miembro de `COleObjectFactory` no puedan encontrar un generador de clases definido en el archivo DLL de extensión MFC.

- `AfxDoForAllClasses` no funciona para las clases en el archivo DLL de extensión MFC.

- La base de datos MFC estándar, sockets o recursos OLE producirá un error al cargar. Por ejemplo, **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) devuelve una cadena vacía, incluso cuando el archivo DLL MFC utiliza correctamente las clases de base de datos de MFC.

La solución a estos problemas es crear y exportar una función de inicialización en la extensión MFC DLL que se crea un **CDynLinkLibrary** objeto. Llame a esta función de inicialización exactamente una vez cada DLL de MFC estándar utiliza el archivo DLL de extensión MFC.

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>OLE de MFC, la base de datos MFC (o DAO) o soporte técnico de Sockets de MFC

Si está utilizando OLE de MFC, MFC base de datos (o DAO) o Sockets de MFC se admite en la DLL de MFC regular, respectivamente, la depuración MFC MFCOxxD.dll archivos DLL de extensión de MFC, MFCDxxD.dll y MFCNxxD.dll (donde xx es el número de versión) se vinculan automáticamente. Debe llamar a una función de inicialización predefinido para cada uno de estos archivos DLL que está usando.

Para obtener soporte técnico de la base de datos, agregue una llamada a `AfxDbInitModule` a su MFC DLL regular `CWinApp::InitInstance` función. Asegúrese de que esta llamada se produce antes de cualquier llamada de clase base o cualquier código que acceda a MFCDxxD.dll agregado. Esta función no toma ningún parámetro y devuelve un valor nulo.

Compatibilidad con OLE, agregue una llamada a `AfxOleInitModule` a su MFC DLL regular `CWinApp::InitInstance`. Tenga en cuenta que el **COleControlModule InitInstance** llamadas de función `AfxOleInitModule` ya, por lo tanto si está creando un control OLE y usas `COleControlModule`, no debe agregar esta llamada a `AfxOleInitModule`.

Para obtener soporte Sockets, agregue una llamada a `AfxNetInitModule` a su MFC DLL regular `CWinApp::InitInstance`.

Tenga en cuenta que las compilaciones de versión de DLL de MFC y aplicaciones no utilizan archivos DLL independientes para la base de datos, sockets, o admitir OLE. Sin embargo, es seguro llamar a estas funciones de inicialización en modo de lanzamiento.

## <a name="cdynlinklibrary-objects"></a>Objetos CDynLinkLibrary

Durante cada una de las operaciones que se ha mencionado al principio de este tema, MFC debe buscar un valor u objeto deseado. Por ejemplo, durante la deserialización, MFC debe buscar en todas las clases de tiempo de ejecución está disponibles para que coincida con los objetos en el archivo con la clase adecuada de tiempo de ejecución.

Como parte de estas búsquedas, MFC examina todas las DLL de extensión MFC en uso por recorrido de una cadena de **CDynLinkLibrary** objetos. **CDynLinkLibrary** adjuntar automáticamente a una cadena durante su construcción de objetos y se crean por cada archivo DLL de extensión MFC a su vez durante la inicialización. Además, cada módulo (aplicación o DLL de MFC regular) tiene su propia cadena de **CDynLinkLibrary** objetos.

Para una extensión MFC DLL para poder conectar a un **CDynLinkLibrary** cadena, debe crear un **CDynLinkLibrary** objeto en el contexto de cada módulo que utiliza el archivo DLL de extensión MFC. Por lo tanto, si una extensión MFC DLL se va a usar en archivos DLL de MFC estándar, debe proporcionar una función de inicialización exportada que crea un **CDynLinkLibrary** objeto. Cada DLL de MFC regular que usa la extensión de MFC DLL debe llamar a la función de inicialización exportada.

Si una extensión MFC DLL sólo se va a usar desde una aplicación MFC (.exe) y nunca desde un archivo DLL MFC, entonces es suficiente para crear el **CDynLinkLibrary** objeto en de la DLL de extensión MFC `DllMain`. Esto es lo que hace la código del archivo DLL de extensión MFC de Asistente de DLL de MFC. Al cargar un archivo DLL de extensión MFC de forma implícita, `DllMain` carga y se ejecuta antes de que se inicie la aplicación. Cualquier **CDynLinkLibrary** creación se conecta a una cadena predeterminada que la DLL de MFC se reserva para una aplicación MFC.

Tenga en cuenta que es una mala idea tener varios **CDynLinkLibrary** objetos desde un archivo DLL de extensión MFC en una cadena, especialmente si el archivo DLL de extensión MFC se va a descargar dinámicamente de la memoria. No llame a la función de inicialización más de una vez desde cualquier módulo.

## <a name="sample-code"></a>Código de ejemplo

Este código de ejemplo se da por supuesto que la DLL de MFC regular implícitamente se vincula a la DLL de extensión MFC. Esto se consigue mediante la vinculación a la biblioteca de importación (.lib) de la DLL de extensión MFC al generar la DLL de MFC regular.

Las líneas siguientes deben estar en el origen de la DLL de extensión MFC:

```
// YourExtDLL.cpp:

// standard MFC extension DLL routines
#include "afxdllx.h"

static AFX_EXTENSION_MODULE NEAR extensionDLL = { NULL, NULL };

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    if (dwReason == DLL_PROCESS_ATTACH)
    {
        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(extensionDLL, hInstance))
           return 0;
    }
    return 1;   // ok
}

// Exported DLL initialization is run in context of
// application or regular MFC DLL
extern "C" void WINAPI InitYourExtDLL()
{
    // create a new CDynLinkLibrary for this app
    new CDynLinkLibrary(extensionDLL);

    // add other initialization here
}
```

Asegúrese de exportar el **InitYourExtDLL** función. Esto puede realizarse mediante **__declspec (dllexport)** o en el archivo .def de su DLL como sigue:

```
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

Agregue una llamada a la `InitInstance` miembro de la `CWinApp`-objeto derivado de cada DLL de MFC regular con la DLL de extensión MFC:

```
// YourRegularDLL.cpp:

class CYourRegularDLL : public CWinApp
{
public:
    virtual BOOL InitInstance(); // Initialization
    virtual int ExitInstance();  // Termination

    // nothing special for the constructor
    CYourRegularDLL(LPCTSTR pszAppName) : CWinApp(pszAppName) { }
};

BOOL CYourRegularDLL::InitInstance()
{
    // any DLL initialization goes here
    TRACE0("YOUR regular MFC DLL initializing\n");

    // wire any MFC extension DLLs into CDynLinkLibrary chain
    InitYourExtDLL();

    return TRUE;
}
```

### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Inicializar un archivo DLL de extensión MFC](run-time-library-behavior.md#initializing-extension-dlls)

- [Inicializar archivos DLL de MFC estándar](run-time-library-behavior.md#initializing-regular-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Archivos DLL de extensión MFC](extension-dlls.md)

- [Archivos DLL de MFC estándar vinculados estáticamente a MFC](regular-dlls-statically-linked-to-mfc.md)

- [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Usar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Versión de DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)

## <a name="see-also"></a>Vea también

[Archivos DLL de extensión MFC](extension-dlls.md)
