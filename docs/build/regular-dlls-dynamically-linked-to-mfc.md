---
title: "Archivos DLL est&#225;ndar vinculados din&#225;micamente a MFC | Microsoft Docs"
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
  - "AFX_MANAGE_STATE (macro)"
  - "DLL [C++], estándar"
  - "vinculados dinámicamente a DLLs [C++]"
  - "DLL estándar [C++], vinculados dinámicamente a MFC"
  - "versiones de DLL compartidas [C++]"
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Archivos DLL est&#225;ndar vinculados din&#225;micamente a MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los archivos DLL estándar vinculados dinámicamente a MFC utilizan internamente las funciones de MFC y las funciones que se exportan de los mismos se podrán invocar desde archivos ejecutables basados o no en MFC.  Como su propio nombre indica, este tipo de archivo DLL se compila con la biblioteca de vínculos dinámicos de MFC \(conocida también como la versión compartida de MFC\).  Las funciones se suelen exportar desde un archivo DLL estándar mediante la interfaz estándar de C.  
  
 Debe agregar la macro `AFX_MANAGE_STATE` al principio de todas las funciones exportadas desde archivos DLL estándar que se vinculen dinámicamente a MFC para establecer el estado actual del módulo en el del archivo DLL.  Para ello, debe agregar la siguiente línea de código al principio de las funciones exportadas desde el archivo DLL:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 Un archivo DLL estándar vinculado dinámicamente a MFC tiene las siguientes características:  
  
-   Es un nuevo tipo de archivo DLL que se incluyó por primera vez en Visual C\+\+ 4.0.  
  
-   El archivo ejecutable cliente se puede programar en cualquier lenguaje compatible con el uso de archivos DLL \(C, C\+\+, Pascal, Visual Basic, etc.\); no tiene que ser una aplicación MFC.  
  
-   A diferencia de un archivo DLL estándar vinculado estáticamente, este tipo de archivos DLL se vincula dinámicamente al archivo DLL de MFC \(conocido también como el archivo DLL compartido de MFC\).  
  
-   La biblioteca de importación de MFC vinculada a este tipo de archivo DLL es la misma que la utilizada para los archivos DLL de extensión o las aplicaciones que utilizan el archivo DLL de MFC: MFCxx\(D\).lib.  
  
 Los requisitos que debe reunir un archivo DLL estándar vinculado dinámicamente a MFC son los siguientes:  
  
-   Estos archivos DLL se compilan con **\_AFXDLL** definido, de la misma manera que un archivo ejecutable que se vincula dinámicamente al archivo DLL de MFC.  Pero también se define **\_USRDLL**, igual que un archivo DLL estándar vinculado estáticamente a MFC.  
  
-   Este tipo de DLL debe crear una instancia de una clase derivada de `CWinApp`.  
  
-   Este tipo de archivo DLL utiliza la función `DllMain` proporcionada por MFC.  Coloque todo el código de inicialización específico del archivo DLL en la función miembro `InitInstance` y el código de finalización en `ExitInstance`, como en una aplicación MFC normal.  
  
 Como este tipo de DLL utiliza la versión de biblioteca de vínculos dinámicos de MFC, deberá establecer explícitamente el estado actual del módulo en el del archivo DLL.  Para ello, utilice la macro [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) al principio de cada función exportada desde el archivo DLL.  
  
 Los archivos DLL estándar deben contener una clase derivada de `CWinApp` y un solo objeto de dicha clase de aplicación, como sucede en una aplicación MFC.  Sin embargo, el objeto `CWinApp` del archivo DLL no tiene un suministro principal de mensajes, como el objeto `CWinApp` de una aplicación.  
  
 Tenga en cuenta que el mecanismo `CWinApp::Run` no se aplica a un archivo DLL, ya que la aplicación es propietaria del suministro principal de mensajes.  Si el archivo DLL muestra cuadros de diálogo no modales o tiene una ventana de marco principal propia, el suministro principal de mensajes de la aplicación deberá llamar a una rutina exportada desde un archivo DLL que, a su vez, llame a `CWinApp::PreTranslateMessage`.  
  
 Coloque todo el código de inicialización específico del archivo DLL en la función miembro `CWinApp::InitInstance`, como en una aplicación MFC normal.  Antes de descargar la DLL, se llamará a la función miembro `CWinApp::ExitInstance` de la clase derivada `CWinApp` desde la función `DllMain` proporcionada por MFC.  
  
 Deberá distribuir con la aplicación los archivos DLL compartidos MFCx0.dll y Msvcr\*0.dll \(o archivos similares\).  
  
 Un archivo DLL vinculado dinámicamente a MFC no puede vincularse también estáticamente.  Las aplicaciones se vinculan a archivos DLL estándar vinculados dinámicamente a MFC, como cualquier otro archivo DLL.  
  
 Los símbolos se suelen exportar desde un archivo DLL estándar mediante la interfaz estándar de C.  La declaración de una función exportada desde un archivo DLL estándar se parecerá a la siguiente:  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 Todas las asignaciones de memoria de un archivo DLL estándar deben permanecer dentro del mismo; no debe haber transferencias entre el archivo DLL y el ejecutable de llamada de:  
  
-   punteros a objetos MFC  
  
-   punteros a memoria asignada por MFC  
  
 Si necesita transferir estos punteros o tiene que pasar objetos derivados de MFC entre el archivo ejecutable de llamada y el archivo DLL, deberá compilar un archivo DLL de extensión.  
  
 La transferencia a memoria de punteros asignados por las bibliotecas en tiempo de ejecución de C entre una aplicación y un archivo DLL sólo será segura si hace una copia de los datos.  No debe eliminar ni cambiar el tamaño de estos punteros, ni utilizarlos sin hacer una copia de la memoria.  
  
 Al compilar un archivo DLL estándar que se vincule dinámicamente a MFC, tendrá que utilizar la macro [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) para cambiar correctamente el estado del módulo de MFC.  Para ello, debe agregar la siguiente línea de código al principio de las funciones exportadas desde el archivo DLL:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 No se debe utilizar la macro **AFX\_MANAGE\_STATE**  en archivos DLL estándar que se vinculen estáticamente a MFC ni en archivos DLL de extensión.  Para obtener más información, vea [Administrar los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md).  
  
 Para consultar un ejemplo que ilustra la forma de programar, compilar y utilizar archivos DLL estándar, vea el ejemplo [DLLScreenCap](http://msdn.microsoft.com/es-es/2171291d-3a50-403b-90a1-d93c2acb4f4a).  Para obtener más información acerca de los archivos DLL estándar que se vinculan dinámicamente a MFC, vea la sección titulada "Convertir DLLScreenCap para que se vincule dinámicamente a un archivo DLL de MFC" en el resumen descriptivo del ejemplo.  
  
## ¿Qué desea hacer?  
  
-   [Inicializar archivos DLL estándar](../build/initializing-regular-dlls.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Estados de módulos de un archivo DLL estándar vinculado dinámicamente a MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
  
-   [Administrar los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [Utilizar archivos DLL de extensión de base de datos, OLE y Sockets en archivos DLL estándar](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [Utilizar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
## Vea también  
 [Tipos de archivos DLL](../build/kinds-of-dlls.md)