---
title: Uso de archivos DLL de extensión MFC de base de datos, OLE y Sockets en archivos DLL de MFC normales
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
ms.openlocfilehash: d08822a04abe5a01883ad8aa1bd6d94269e810cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314694"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>Uso de archivos DLL de extensión MFC de base de datos, OLE y Sockets en archivos DLL de MFC normales

Cuando se usa un archivo DLL de extensión MFC desde un archivo DLL de MFC estándar, si el archivo DLL de extensión MFC no está conectado a la cadena de objetos **CDynLinkLibrary** del archivo DLL de MFC estándar, podría encontrarse con uno o varios problemas relacionados. Dado que las versiones de depuración de la base de datos MFC, OLE y Sockets que admiten archivos DLL se implementan como archivos DLL de extensión MFC, es posible que vea problemas similares si usa estas características de MFC, incluso si no usa explícitamente ninguno de sus propios archivos DLL de extensión MFC. Algunos de los síntomas son los siguientes:

- Al intentar deserializar un objeto de un tipo de clase definido en el archivo DLL de extensión MFC, aparecerá el mensaje "Advertencia: No se puede cargar CYourClass desde el archivo. Clase sin definir" en la ventana de depuración de seguimiento y el objeto no se puede serializar.

- Se puede producir una excepción que indica una clase incorrecta.

- Los recursos almacenados en el archivo DLL de extensión MFC no se pueden cargar porque `AfxFindResourceHandle` devuelve **NULL** o un manipulador de recurso incorrecto.

- `DllGetClassObject`, `DllCanUnloadNow` y las funciones miembro `UpdateRegistry`, `Revoke`, `RevokeAll` y `RegisterAll` de `COleObjectFactory` no pueden encontrar un generador de clases definido en el archivo DLL de extensión MFC.

- `AfxDoForAllClasses` no funciona para ninguna clase en el archivo DLL de extensión MFC.

- La base de datos MFC estándar, los sockets o los recursos OLE no se pueden cargar. Por ejemplo, **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) devuelve una cadena vacía, incluso cuando el archivo DLL de MFC estándar usa correctamente las clases de base de datos MFC.

La solución a estos problemas es crear y exportar una función de inicialización en el archivo DLL de extensión MFC que crea un objeto **CDynLinkLibrary**. Llame a esta función de inicialización exactamente una vez desde cada archivo DLL de MFC estándar que use el archivo DLL de extensión MFC.

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>Compatibilidad con OLE de MFC, base de datos MFC (o DAO) o sockets MFC

Si utiliza cualquier compatibilidad con OLE de MFC, base de datos MFC (o DAO) o sockets MFC en el archivo DLL de MFC estándar, respectivamente, los archivos DLL de extensión MFC de depuración de MFC MFCOxxD.dll, MFCDxxD.dll y MFCNxxD.dll (donde xx es el número de versión) se vinculan automáticamente. Se debe llamar a una función de inicialización predefinida para cada uno de estos archivos DLL que se usen.

En el caso de la compatibilidad con la base de datos, agregue una llamada a `AfxDbInitModule` a la función `CWinApp::InitInstance` de los archivos DLL de MFC estándar. Asegúrese de que esta llamada se produce antes que cualquier llamada de clase base o cualquier código agregado que tenga acceso al archivo MFCDxxD.dll. Esta función no toma ningún parámetro y devuelve void.

En el caso de la compatibilidad con OLE, agregue una llamada a `AfxOleInitModule` a la función `CWinApp::InitInstance` de los archivos DLL de MFC estándar. Tenga en cuenta que la función **COleControlModule InitInstance** ya llama a `AfxOleInitModule`, por lo que si se está compilando un control OLE y se está usando `COleControlModule`, no se debe agregar esta llamada a `AfxOleInitModule`.

En el caso de la compatibilidad con sockets, agregue una llamada a `AfxNetInitModule` a la función `CWinApp::InitInstance` de los archivos DLL de MFC estándar.

Tenga en cuenta que las compilaciones de versión de las aplicaciones y archivos DLL de MFC no usan archivos DLL independientes para la compatibilidad con la base de datos, OLE o sockets. Sin embargo, es seguro llamar a estas funciones de inicialización en modo de versión.

## <a name="cdynlinklibrary-objects"></a>Objetos CDynLinkLibrary

Durante cada una de las operaciones mencionadas al principio de este tema, MFC necesita buscar un valor o un objeto deseado. Por ejemplo, durante la deserialización, MFC necesita buscar en todas las clases en tiempo de ejecución actualmente disponibles para que los objetos del archivo coincidan con su clase en tiempo de ejecución adecuada.

Como parte de estas búsquedas, MFC examina todos los archivos DLL de extensión MFC en uso recorriendo una cadena de objetos **CDynLinkLibrary**. Los objetos **CDynLinkLibrary** se asocian automáticamente a una cadena durante su construcción y cada archivo DLL de extensión MFC los crea a su vez durante la inicialización. Además, cada módulo (aplicación o archivo DLL de MFC estándar) tiene su propia cadena de objetos **CDynLinkLibrary**.

Para que un archivo DLL de extensión MFC se conecte a una cadena **CDynLinkLibrary**, debe crear un objeto **CDynLinkLibrary** en el contexto de cada módulo que utilice el archivo DLL de extensión MFC. Por lo tanto, si se va a utilizar un archivo DLL de extensión MFC desde archivos DLL de MFC estándar, debe proporcionar una función de inicialización exportada que cree un objeto **CDynLinkLibrary**. Cada archivo DLL de MFC estándar que use el archivo DLL de extensión MFC debe llamar a la función de inicialización exportada.

Si un archivo DLL de extensión MFC solo se va a usar desde una aplicación MFC (.exe) y nunca desde un archivo DLL de MFC estándar, será suficiente para crear el objeto **CDynLinkLibrary** en el elemento `DllMain` del archivo DLL de extensión MFC. Esto es lo que hace el código DLL de extensión MFC del Asistente para archivos DLL de MFC. Al cargar un archivo DLL de extensión MFC de manera implícita, `DllMain` se carga y ejecuta antes de que se inicie la aplicación. Cualquier creación **CDynLinkLibrary** se conecta a una cadena predeterminada que el archivo DLL de MFC reserva para una aplicación MFC.

Tenga en cuenta que no es recomendable tener varios objetos **CDynLinkLibrary** de un archivo DLL de extensión MFC en una cadena, especialmente si este archivo se va a descargar dinámicamente de la memoria. No llame a la función de inicialización más de una vez desde cada módulo.

## <a name="sample-code"></a>Código de ejemplo

En este código de ejemplo se supone que el archivo DLL de MFC estándar está vinculando implícitamente al archivo DLL de extensión MFC. Esto se logra mediante la vinculación a la biblioteca de importación (.lib) del archivo DLL de extensión MFC cuando se compila el archivo DLL de MFC estándar.

Las líneas siguientes deben estar en el código fuente del archivo DLL de extensión MFC:

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

Asegúrese de exportar la función **InitYourExtDLL**. Esto puede realizarse mediante **__declspec (dllexport)** o en el archivo .def del DLL de la siguiente manera:

```
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

Agregue una llamada al miembro `InitInstance` del objeto derivado de `CWinApp` en cada archivo DLL de MFC estándar mediante el archivo DLL de extensión MFC:

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
