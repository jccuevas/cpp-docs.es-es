---
title: Usar archivos DLL de extensión de base de datos, OLE y Sockets de MFC en archivos DLL de MFC estándar | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0042dd5dc6049447868cf5ca5ea1112b3695f3a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>Utilizar archivos DLL de extensión de base de datos, OLE y Sockets de MFC en archivos DLL de MFC estándar
Cuando se usa una extensión MFC DLL desde una DLL de MFC normal, si la extensión MFC DLL no está conectada a la **CDynLinkLibrary** cadena del objeto de la DLL de MFC regulares, puede ejecutar en uno o más de una serie de problemas relacionados. Dado que admiten las versiones de depuración de la base de datos de MFC, OLE y Sockets archivos DLL se implementan como archivos DLL de extensión MFC, podría ver problemas similares si usa estos MFC características, incluso si explícitamente no usa cualquiera de su propios archivos DLL de extensión MFC. Algunos síntomas son:  
  
-   Al intentar deserializar un objeto de un tipo de clase definido en la extensión MFC DLL, el mensaje "Advertencia: no se puede cargar CSuClase desde el archivo. Clase no definida". aparece en la ventana de depuración de seguimiento y el objeto no se puede serializar.  
  
-   Podría producirse una excepción que indica la clase incorrecto.  
  
-   Recursos almacenados en el archivo DLL de extensión MFC no se pudo cargar porque `AfxFindResourceHandle` devuelve **NULL** o un identificador de recursos incorrecto.  
  
-   `DllGetClassObject`, `DllCanUnloadNow`y el `UpdateRegistry`, `Revoke`, `RevokeAll`, y `RegisterAll` las funciones miembro de `COleObjectFactory` no puedan encontrar un generador de clases definido en el archivo DLL de extensión MFC.  
  
-   `AfxDoForAllClasses`no funciona para todas las clases en el archivo DLL de extensión MFC.  
  
-   La base de datos MFC estándar, sockets u OLE recursos no cargará. Por ejemplo, **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) devuelve una cadena vacía, incluso cuando la DLL de MFC normal se utiliza correctamente las clases de base de datos de MFC.  
  
 La solución a estos problemas es crear y exportar una función de inicialización en la extensión MFC DLL que crea un **CDynLinkLibrary** objeto. Llame a esta función de inicialización exactamente una vez cada DLL de MFC estándar utiliza el archivo DLL de extensión MFC.  
  
## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>OLE de MFC, la base de datos MFC (o DAO) o MFC Sockets de soporte técnico  
 Si está utilizando MFC OLE, MFC Database (o DAO) o Sockets de MFC se admite en la DLL de MFC normal, respectivamente, la depuración MFC MFCOxxD.dll archivos DLL de extensión de MFC, MFCDxxD.dll y MFCNxxD.dll (donde xx es el número de versión) se vinculan automáticamente. Debe llamar a una función de inicialización predefinidas para cada uno de estos archivos DLL que está usando.  
  
 Compatibilidad de base de datos, agregue una llamada a `AfxDbInitModule` a su MFC DLL regular `CWinApp::InitInstance` función. Asegúrese de que esta llamada se produce antes de cualquier llamada de clase base o cualquier código agregado que acceda a MFCDxxD.dll. Esta función no toma ningún parámetro y devuelve un valor nulo.  
  
 Para la compatibilidad con OLE, agregue una llamada a `AfxOleInitModule` a su MFC DLL regular `CWinApp::InitInstance`. Tenga en cuenta que la **COleControlModule InitInstance** llamadas a funciones `AfxOleInitModule` ya, por lo que si está generando un control OLE y utiliza `COleControlModule`, no debe agregar esta llamada a `AfxOleInitModule`.  
  
 Para ofrecer compatibilidad con Sockets, agregue una llamada a `AfxNetInitModule` a su MFC DLL regular `CWinApp::InitInstance`.  
  
 Tenga en cuenta que las versiones de lanzamiento de los archivos DLL de MFC y aplicaciones no utilizan archivos DLL independientes para la base de datos, sockets, o compatible con OLE. Sin embargo, resulta seguro llamar a estas funciones de inicialización en modo de lanzamiento.  
  
## <a name="cdynlinklibrary-objects"></a>Objetos CDynLinkLibrary  
 Durante cada una de las operaciones mencionadas al principio de este tema, MFC debe buscar un valor u objeto deseado. Por ejemplo, durante la deserialización, MFC debe buscar en todas las clases de tiempo de ejecución está disponibles para que coincida con los objetos en el archivo con su clase de tiempo de ejecución adecuada.  
  
 Como parte de estas búsquedas, MFC recorre todas las DLL de extensión MFC en uso recorriendo una cadena de **CDynLinkLibrary** objetos. **CDynLinkLibrary** objetos se asocian automáticamente a una cadena durante su construcción y se crean por cada archivo DLL de extensión MFC a su vez durante la inicialización. Además, cada módulo (aplicación o DLL de MFC regular) tiene su propia cadena de **CDynLinkLibrary** objetos.  
  
 Para una extensión MFC DLL para poder conectar a un **CDynLinkLibrary** cadena, debe crear un **CDynLinkLibrary** objeto en el contexto de cada módulo que utilice el archivo DLL de extensión MFC. Por lo tanto, si una extensión MFC DLL se va a utilizarse desde archivos DLL estándar de MFC, debe proporcionar una función de inicialización exportada que crea un **CDynLinkLibrary** objeto. Cada DLL MFC estándar que utiliza la extensión MFC DLL debe llamar a la función de inicialización exportada.  
  
 Si una extensión MFC DLL solo se va a usar desde una aplicación MFC (.exe) y nunca desde una DLL de MFC normal, es suficiente para crear la **CDynLinkLibrary** objeto en de la DLL de extensión MFC `DllMain`. Esto es lo que hace el código del archivo DLL de extensión de MFC de Asistente para archivos DLL de MFC. Al cargar un archivo DLL de extensión MFC implícitamente, `DllMain` carga y ejecuta antes de que se inicie la aplicación. Cualquier **CDynLinkLibrary** creación se conecta a una cadena predeterminada que la DLL de MFC se reserva para una aplicación MFC.  
  
 Tenga en cuenta que es una buena idea tener varios **CDynLinkLibrary** objetos desde un archivo DLL de extensión MFC en una cadena, especialmente si el archivo DLL de extensión MFC se descargará dinámicamente de la memoria. No llame a la función de inicialización más de una vez desde cualquier módulo.  
  
## <a name="sample-code"></a>Código de ejemplo  
 Este código de ejemplo se da por supuesto que la DLL de MFC normal se vincula implícitamente al archivo DLL de extensión MFC. Esto se consigue mediante la vinculación a la biblioteca de importación (.lib) de la DLL de extensión MFC al generar la DLL de MFC normal.  
  
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
  
 Asegúrese de exportar la **InitYourExtDLL** función. Esto puede realizarse mediante **__declspec (dllexport)** o en el archivo .def de su DLL como sigue:  
  
```  
// YourExtDLL.Def:  
LIBRARY      YOUREXTDLL  
CODE         PRELOAD MOVEABLE DISCARDABLE  
DATA         PRELOAD SINGLE  
EXPORTS  
    InitYourExtDLL  
```  
  
 Agregue una llamada a la `InitInstance` miembro de la `CWinApp`-objeto en cada DLL de MFC estándar mediante el archivo DLL de extensión MFC derivado:  
  
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
  
-   [Inicializar un archivo DLL de extensión MFC](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
-   [Inicializar archivos DLL de MFC estándar](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Archivos DLL de extensión MFC](../build/extension-dlls.md)  
  
-   [Archivos DLL de MFC estándar vinculados estáticamente a MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Utilizar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [Versión del archivo DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL de extensión MFC](../build/extension-dlls.md)