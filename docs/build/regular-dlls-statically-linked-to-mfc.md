---
title: "Archivos DLL est&#225;ndar vinculados est&#225;ticamente a MFC | Microsoft Docs"
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
  - "DLL [C++], estándar"
  - "DLL estándar [C++]"
  - "DLL estándar [C++], vinculados estáticamente a MFC"
  - "DLLs vinculadas estáticamente [C++]"
  - "USRDLL"
  - "USRDLL, vinculados estáticamente a MFC"
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Archivos DLL est&#225;ndar vinculados est&#225;ticamente a MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los archivos DLL estándar vinculados estáticamente a MFC utilizan internamente las funciones de MFC y las funciones que se exportan de los mismos podrán llamarse desde archivos ejecutables basados o no en MFC.  Como su propio nombre indica, este tipo de archivo DLL se compila con la biblioteca de vínculos estáticos de MFC.  Las funciones se suelen exportar desde un archivo DLL estándar mediante la interfaz estándar de C.  Para consultar un ejemplo que ilustra la forma de programar, compilar y utilizar archivos DLL estándar, vea el ejemplo [DLLScreenCap](http://msdn.microsoft.com/es-es/2171291d-3a50-403b-90a1-d93c2acb4f4a).  
  
 Tenga en cuenta que en la documentación de Visual C\+\+ ya no se utiliza el término USRDLL.  Un archivo DLL estándar vinculado estáticamente a MFC tiene las mismas características que el antiguo archivo USRDLL.  
  
 Un archivo DLL estándar, vinculado estáticamente a MFC, presenta las siguientes características:  
  
-   El archivo ejecutable cliente se puede programar en cualquier lenguaje compatible con el uso de archivos DLL \(C, C\+\+, Pascal, Visual Basic, etc.\); no tiene que ser una aplicación MFC.  
  
-   El archivo DLL puede vincularse a las mismas bibliotecas de vínculos estáticos de MFC que utilizan las aplicaciones.  Ya no existe una versión independiente de las bibliotecas de vínculos estáticos para archivos DLL.  
  
-   Antes de la versión 4.0 de MFC, los archivos USRDLL proporcionaban el mismo tipo de funcionalidad que los archivos DLL estándar vinculados estáticamente a MFC.  A partir de Visual C\+\+ versión 4.0, el término USRDLL ha quedado obsoleto.  
  
 Los requisitos que debe reunir un archivo DLL estándar vinculado estáticamente a MFC son los siguientes:  
  
-   Este tipo de archivo DLL debe crear una instancia de una clase derivada de `CWinApp`.  
  
-   Este tipo de archivo DLL utiliza la función `DllMain` proporcionada por MFC.  Coloque todo el código de inicialización específico del archivo DLL en la función miembro `InitInstance` y el código de finalización en `ExitInstance`, como en una aplicación MFC normal.  
  
-   Aunque ahora el término USRDLL haya quedado obsoleto, todavía tendrá que definir "**\_USRDLL**" en la línea de comandos del compilador.  Esta definición determina las declaraciones que se van a extraer de los archivos de encabezado de MFC.  
  
 Los archivos DLL estándar deben contener una clase derivada de `CWinApp` y un solo objeto de dicha clase de aplicación, como sucede en una aplicación MFC.  Sin embargo, el objeto `CWinApp` del archivo DLL no tiene un suministro principal de mensajes, como el objeto `CWinApp` de una aplicación.  
  
 Tenga en cuenta que el mecanismo `CWinApp::Run` no se aplica a un archivo DLL, ya que la aplicación es propietaria del suministro principal de mensajes.  Si el archivo DLL abre cuadros de diálogo no modales o tiene una ventana de marco principal propia, el suministro principal de mensajes de la aplicación debe llamar a una rutina exportada por el archivo DLL que, a su vez, llama a la función miembro `CWinApp::PreTranslateMessage` del objeto de aplicación del archivo DLL.  
  
 Si desea analizar un ejemplo del uso de esta función, vea el ejemplo DLLScreenCap.  
  
 Los símbolos se suelen exportar desde un archivo DLL estándar mediante la interfaz estándar de C.  La declaración de una función exportada desde un archivo DLL estándar se parecerá a la siguiente:  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 Todas las asignaciones de memoria de un archivo DLL estándar deben permanecer dentro del mismo; no debe haber transferencias entre el archivo DLL y el ejecutable de llamada de:  
  
-   Punteros a objetos MFC  
  
-   Punteros a memoria asignada por MFC  
  
 Si necesita transferir estos punteros o tiene que pasar objetos derivados de MFC entre el archivo ejecutable de llamada y el archivo DLL, deberá compilar un archivo DLL de extensión.  
  
 La transferencia a memoria de punteros asignados por las bibliotecas en tiempo de ejecución de C entre una aplicación y un archivo DLL sólo será segura si hace una copia de los datos.  No debe eliminar ni cambiar el tamaño de estos punteros, ni utilizarlos sin hacer una copia de la memoria.  
  
 Un archivo DLL vinculado estáticamente a MFC no puede vincularse también dinámicamente a los archivos DLL compartidos de MFC.  Un archivo DLL vinculado estáticamente a MFC se enlaza dinámicamente a una aplicación de la misma manera que cualquier otro archivo DLL; las aplicaciones se vinculan al archivo DLL como a cualquier otro archivo DLL.  
  
 Los nombres de las bibliotecas de vínculos estáticos estándar de MFC siguen la convención que se describe en el tema [Convenciones de nomenclatura para archivos DLL de MFC](../build/naming-conventions-for-mfc-dlls.md).  No obstante, con la versión 3.0 de MFC y versiones posteriores, ya no es necesario especificar manualmente en el vinculador la versión de la biblioteca MFC que se desea vincular.  En su lugar, los archivos de encabezado MFC determinan automáticamente la versión correcta de la biblioteca MFC con la que se debe vincular según las definiciones del preprocesador, tales como **\_DEBUG** o **\_UNICODE**.  Los archivos de encabezado de MFC agregan directivas \/DEFAULTLIB que indican al vinculador que debe vincular una versión específica de la biblioteca MFC.  
  
## ¿Qué desea hacer?  
  
-   [Inicializar archivos DLL estándar](../build/initializing-regular-dlls.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Utilizar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [Utilizar archivos DLL de extensión de base de datos, OLE y Sockets en archivos DLL estándar](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [Crear un archivo DLL compatible con MFC](../mfc/reference/mfc-dll-wizard.md)  
  
-   [Archivos DLL estándar vinculados dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Archivos DLL de extensión](../build/extension-dlls-overview.md)  
  
## Vea también  
 [Tipos de archivos DLL](../build/kinds-of-dlls.md)