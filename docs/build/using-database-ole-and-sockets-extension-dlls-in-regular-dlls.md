---
title: "Utilizar archivos DLL de extensi&#243;n de base de datos, OLE y Sockets en archivos DLL est&#225;ndar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], extensión"
  - "DLL [C++], inicializar"
  - "DLL [C++], estándar"
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Utilizar archivos DLL de extensi&#243;n de base de datos, OLE y Sockets en archivos DLL est&#225;ndar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al utilizar un archivo DLL de extensión desde un archivo DLL estándar, si el archivo DLL de extensión no está conectado a la cadena de objetos **CDynLinkLibrary** del archivo DLL estándar, pueden producirse uno o más problemas relacionados.  Como las versiones de depuración de los archivos DLL de compatibilidad con MFC Database, MFC OLE y MFC Sockets se implementan como archivos DLL de extensión, podrían producirse problemas si utiliza estas características de MFC, aunque no utilice explícitamente ninguno de sus archivos DLL de extensión.  Algunos síntomas son los siguientes:  
  
-   Si intenta deserializar un objeto de un tipo de clase definida en el archivo DLL de extensión, el mensaje "Advertencia: no se puede cargar CSuClase desde el archivo de almacenamiento.  Clase no definida." aparece en la ventana de depuración de seguimiento \(TRACE\) y la operación de serialización del objeto no se realiza.  
  
-   Podría producirse una excepción que indique que la clase es errónea.  
  
-   No se pueden cargar los recursos almacenados en el archivo DLL de extensión porque `AfxFindResourceHandle` devuelve **NULL** o un identificador de recursos incorrecto.  
  
-   `DllGetClassObject`, `DllCanUnloadNow` y las funciones miembro `UpdateRegistry`, `Revoke`, `RevokeAll` y `RegisterAll` de `COleObjectFactory` no pueden encontrar el generador de clases definido en el archivo DLL de extensión.  
  
-   `AfxDoForAllClasses` no funciona con ninguna clase del archivo DLL de extensión.  
  
-   No se pueden cargar los recursos estándar de MFC Database, MFC Sockets o MFC OLE.  Por ejemplo, **AfxLoadString**\(**AFX\_IDP\_SQL\_CONNECT\_FAIL**\) devuelve una cadena vacía, incluso cuando el archivo DLL estándar utiliza correctamente las clases de MFC Database.  
  
 La solución de estos problemas es crear y exportar una función de inicialización en el archivo DLL de extensión que crea un objeto **CDynLinkLibrary**.  Debe llamar a esta función de inicialización una vez para cada archivo DLL estándar que utilice el archivo DLL de extensión.  
  
## Compatibilidad con MFC OLE, MFC Database \(o DAO\) y MFC Sockets  
 Si utiliza la compatibilidad con MFC OLE, MFC Database \(o DAO\) o MFC Sockets en el archivo DLL estándar, se vincularán automáticamente los archivos DLL de extensión para depuración de MFC MFCOxxD.dll, MFCDxxD.dll y MFCNxxD.dll \(donde xx es el número de versión\), respectivamente.  Debe llamar a una función de inicialización predefinida para cada uno de los archivos DLL que utilice.  
  
 Para ofrecer compatibilidad con bases de datos, agregue una llamada a `AfxDbInitModule` a la función `CWinApp::InitInstance` del archivo DLL estándar.  Asegúrese de que esta llamada se realiza antes de cualquier llamada de clase base o cualquier código agregado que obtenga acceso a MFCDxxD.dll.  Esta función no usa parámetros y devuelve un tipo void.  
  
 Para ofrecer compatibilidad con OLE, agregue una llamada a `AfxOleInitModule` a la función `CWinApp::InitInstance` del archivo DLL estándar.  Tenga en cuenta que la función **COleControlModule InitInstance** ya llama a `AfxOleInitModule`, por lo que si está compilando un control OLE y utiliza `COleControlModule`, no debe agregar esta llamada a `AfxOleInitModule`.  
  
 Para ofrecer compatibilidad con Sockets, agregue una llamada a `AfxNetInitModule` a la función `CWinApp::InitInstance` del archivo DLL estándar.  
  
 Tenga en cuenta que las versiones de lanzamiento de los archivos DLL de MFC no utilizan archivos DLL separados para ofrecer compatibilidad con bases de datos, sockets u OLE.  Sin embargo, es seguro llamar a estas funciones de inicialización en modo de versión lanzamiento.  
  
## Objetos CDynLinkLibrary  
 Durante cada una de las operaciones mencionadas al principio de este tema, MFC debe buscar un valor u objeto deseado.  Por ejemplo, durante la deserialización, MFC debe buscar en todas las clases en tiempo de ejecución disponibles objetos del archivo de almacenamiento coincidentes con la clase en tiempo de ejecución apropiada.  
  
 Como parte de estas búsquedas, MFC recorre una cadena de objetos **CDynLinkLibrary** en todos los archivos DLL de extensión utilizados.  Los objetos **CDynLinkLibrary** se asocian automáticamente a una cadena durante su construcción y se crean mediante cada archivo DLL de extensión durante la inicialización.  Además, cada módulo \(aplicación o archivo DLL estándar\) tiene su propia cadena de objetos **CDynLinkLibrary**.  
  
 Para poder conectar un archivo DLL de extensión a una cadena **CDynLinkLibrary**, debe crear un objeto **CDynLinkLibrary** en el contexto de cada módulo que utilice el archivo DLL de extensión.  Por tanto, si va a utilizar el archivo DLL de extensión desde archivos DLL estándar, deberá exportar una función de inicialización exportada que cree un objeto **CDynLinkLibrary**.  Cada DLL estándar que utilice el archivo DLL de extensión debe llamar a la función de inicialización exportada.  
  
 Si un archivo DLL de extensión sólo se va a utilizar desde una aplicación MFC \(.exe\), nunca desde un archivo DLL estándar, es suficiente con crear el objeto **CDynLinkLibrary** en la función `DllMain` del archivo DLL de extensión.  Esto es lo que hace el código del archivo DLL de extensión del Asistente para archivos DLL de MFC.  Al cargar un archivo DLL de extensión implícitamente, se carga y ejecuta `DllMain` antes de que se inicie la aplicación.  Cualquier creación de **CDynLinkLibrary** se conecta a una cadena predeterminada que reserva el archivo DLL de MFC para cualquier aplicación MFC.  
  
 Tenga en cuenta que no es recomendable utilizar varios objetos **CDynLinkLibrary** de un archivo DLL de extensión en una cadena, especialmente si se va a descargar dinámicamente de la memoria el archivo DLL de extensión.  No llame a la función de inicialización más de una vez desde cualquier módulo.  
  
## Código de ejemplo  
 En este código de ejemplo se supone que el archivo DLL estándar se vincula implícitamente al archivo DLL de extensión.  Esto se consigue estableciendo un vínculo con la biblioteca de importación \(.lib\) del archivo DLL de extensión al compilar el archivo DLL estándar.  
  
 El código fuente del archivo DLL de extensión debe incluir las siguientes líneas:  
  
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
        // extension DLL one-time initialization  
        if (!AfxInitExtensionModule(extensionDLL, hInstance))  
           return 0;  
    }  
    return 1;   // ok  
}  
  
// Exported DLL initialization is run in context of  
// application or regular DLL  
extern "C" void WINAPI InitYourExtDLL()  
{  
    // create a new CDynLinkLibrary for this app  
    new CDynLinkLibrary(extensionDLL);  
  
    // add other initialization here  
}  
```  
  
 Asegúrese de exportar la función **InitYourExtDLL**.  Puede hacerlo mediante **\_\_declspec\(dllexport\)** o en el archivo .def del archivo DLL, de la siguiente manera:  
  
```  
// YourExtDLL.Def:  
LIBRARY      YOUREXTDLL  
CODE         PRELOAD MOVEABLE DISCARDABLE  
DATA         PRELOAD SINGLE  
EXPORTS  
    InitYourExtDLL  
```  
  
 Agregue una llamada al miembro `InitInstance` del objeto derivado de `CWinApp` en cada DLL estándar mediante el archivo DLL de extensión:  
  
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
    TRACE0("YOUR regular DLL initializing\n");  
  
    // wire any extension DLLs into CDynLinkLibrary chain  
    InitYourExtDLL();  
  
    return TRUE;  
}  
```  
  
### ¿Qué desea hacer?  
  
-   [Inicializar un archivo DLL de extensión](../build/initializing-extension-dlls.md)  
  
-   [Inicializar archivos DLL estándar](../build/initializing-regular-dlls.md)  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Archivos DLL de extensión](../build/extension-dlls.md)  
  
-   [Archivos DLL estándar vinculados estáticamente a MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Archivos DLL estándar vinculados dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Utilizar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [Versión de DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)  
  
## Vea también  
 [Archivos DLL de extensión](../build/extension-dlls.md)