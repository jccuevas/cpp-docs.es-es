---
title: "TN011: Usar MFC como parte de un archivo DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.dll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_USRDLL (símbolo)"
  - "DLL [C++], vincular"
  - "DLL de MFC [C++], vincular las DLL normales a MFC"
  - "TN011"
  - "USRDLL, modificadores del compilador"
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
caps.latest.revision: 20
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN011: Usar MFC como parte de un archivo DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta nota describe los archivos DLL estándar, que le permiten utilizar la biblioteca MFC como parte de la biblioteca de vínculos dinámicos \(DLL\) de Windows.  Se supone que está familiarizado con los archivos DLL de Windows y cómo compilarlos.  Para obtener información sobre los archivos DLL de extensión de MFC, con los que podrá crear extensiones a la biblioteca MFC, vea [Versión de DLL de MFC](../mfc/tn033-dll-version-of-mfc.md).  
  
## Interfaces DLL  
 Los archivos DLL estándar suponen que las interfaces entre la aplicación y DLL se especificadas en C como funciones o clases explícitamente exportadas.  Las interfaces de clase MFC no pueden exportar.  
  
 Si el archivo DLL y una aplicación desean utilizar MFC, haga que una opción para utilizar la versión compartida de las bibliotecas MFC o a estáticamente vincula a una copia de las bibliotecas.  La aplicación y DLL pueden ambas utilizar una de las versiones estándar de la biblioteca MFC.  
  
 Los archivos DLL estándar tienen varias ventajas:  
  
-   La aplicación que utiliza el archivo DLL no tiene que utilizar MFC y no tiene que ser una aplicación de Visual C\+\+.  
  
-   Con los archivos DLL estándar vinculados estáticamente a MFC, el tamaño del archivo DLL sólo depende de las rutinas de servicio de c y MFC se utilizan y están vinculados.  
  
-   Con los archivos DLL estándar vinculados dinámicamente a MFC, el ahorro de memoria de utilizar la versión compartida de MFC pueden ser significativos.  Sin embargo, debe distribuir archivos DLL, el MFC*\<version\>*.dll y el Msvvcrt compartidos*\<version\>*.dll, a un archivo DLL.  
  
-   El diseño de DLL es independiente de cómo se implementan las clases.  El diseño de DLL sólo exporta el API que desee.  Como resultado, si la implementación, los archivos DLL estándar siguen siendo válidos.  
  
-   Con los archivos DLL estándar vinculados estáticamente a MFC, si el archivo DLL y la aplicación utiliza MFC, no hay ningún problema con la aplicación que desea una versión diferente de MFC que DLL o viceversa.  Dado que la biblioteca MFC se vincula estáticamente en cada DLL o EXE, no hay ninguna pregunta sobre la versión tiene.  
  
## Limitaciones de la API  
 Algunas funciones de MFC no se aplica a la versión de DLL, o debido a limitaciones técnicas o porque los servicios proporciona normalmente por la aplicación.  Con la versión actual de MFC, la única función que no es aplicable es `CWinApp::SetDialogBkColor`.  
  
## Compilar un archivo DLL  
 Cuando la compilación de archivos DLL estándar vinculados estáticamente a MFC, los símbolos `_USRDLL` y `_WINDLL` debe definirse.  El código del archivo DLL también se debe compilar con los modificadores siguientes del compilador:  
  
-   **\/D\_WINDLL** significa la compilación se para DLL  
  
-   **\/D\_USRDLL** le especifica está compilando el archivo DLL estándar  
  
 También debe definir estos símbolos y utilizar estos modificadores del compilador cuando se compilan los archivos DLL estándar vinculados dinámicamente a MFC.  Además, el símbolo `_AFXDLL` debe estar definido y el código del archivo DLL debe compilarse con:  
  
-   **\/D\_AFXDLL** especifica que está compilando el archivo DLL estándar que se vincule dinámicamente a MFC  
  
 Las interfaces \(API\) entre la aplicación y el archivo DLL deben explícitamente exportar.  Se recomienda definir interfaces para ser ancho banda en, y se utiliza únicamente las interfaces de C si puede.  Las interfaces directas de C son más fáciles de mantener que clases más complejas de C\+\+.  
  
 Coloque las API de un encabezado independiente que se puede incluir en los archivos de c y C\+\+.  Vea el encabezado ScreenCap.h en MFC avanzada de ejemplo [DLLScreenCap](../top/visual-cpp-samples.md) de los conceptos para un ejemplo.  Para exportar las funciones, incorpórelas en la sección de `EXPORTS` del archivo de definición de módulo \(.DEF\) o incluya `__declspec(dllexport)` en las definiciones de función.  Utilice `__declspec(dllimport)` para importar estas funciones en el archivo ejecutable cliente.  
  
 Debe agregar la macro de `AFX_MANAGE_STATE` al principio de todas las funciones exportadas desde archivos DLL estándar vinculados dinámicamente a MFC.  Esta macro establece el estado actual del módulo en el del archivo DLL.  Para utilizar esta macro, agregue la siguiente línea de código al principio de las funciones exportadas desde el archivo DLL:  
  
 `AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`  
  
## WinMain \-\> DllMain  
 La biblioteca MFC define el punto de entrada estándar de Win32 `DllMain` que inicializa el objeto derivado [CWinApp](../mfc/reference/cwinapp-class.md) como una aplicación MFC normal.  Coloque todo el código de inicialización DLL\- concreta en el método de [InitInstance](../Topic/CWinApp::InitInstance.md) como una aplicación MFC normal.  
  
 Tenga en cuenta que el mecanismo [CWinApp::Run](../Topic/CWinApp::Run.md) no se aplica a un archivo DLL, ya que la aplicación es propietaria del suministro principal de mensajes.  Si el archivo DLL muestra cuadros de diálogo no modales o tiene una ventana de marco principal propia, el suministro principal de mensajes de la aplicación debe llamar a una rutina DLL\- exportada que llame a [CWinApp::PreTranslateMessage](../Topic/CWinApp::PreTranslateMessage.md).  
  
 Vea el ejemplo DLLScreenCap para el uso de esta función.  
  
 La función de `DllMain` que MFC proporciona al método de [CWinApp::ExitInstance](../Topic/CWinApp::ExitInstance.md) de la clase que se deriva de `CWinApp` antes de descargar el archivo DLL.  
  
## Vincular DLL  
 Con los archivos DLL estándar vinculados estáticamente a MFC, debe vincular DLL con Nafxcwd.lib o Nafxcw.lib y con la versión de los tiempos de ejecución de C denominados Libcmt.lib.  Estas bibliotecas son pregeneradas y pueden instalarse especificándolos cuando ejecute Visual C\+\+ configurar.  
  
## Código de ejemplo  
 Vea MFC avanzada de programa de ejemplo DLLScreenCap de los conceptos de un ejemplo completo.  Varias cosas interesantes para anotar en este ejemplo:  
  
-   Marcas de DLL y los de la aplicación son diferentes.  
  
-   Las líneas de vínculo y archivos .DEF para DLL y los de la aplicación son diferentes.  
  
-   La aplicación que utiliza el archivo DLL no tiene que estar en C\+\+.  
  
-   La interfaz entre la aplicación y el archivo DLL es una API utilizable por C o C\+\+ y se exporta con DLLScreenCap.def.  
  
 El ejemplo siguiente se muestra la API que se define en un archivo DLL estándar que se vincule estáticamente a MFC.  En este ejemplo, la declaración se agrega en `extern "C" { }` bloqueado para los usuarios de C\+\+.  Esto tiene varias ventajas.  Primero, crea el archivo DLL API utilizable por aplicaciones de cliente que no están programadas.  En segundo lugar, reduce la sobrecarga del archivo porque la destrucción del nombre de C\+\+ no se aplicará el nombre exportado.  Por último, resulta más fácil agregar explícitamente a un archivo .DEF \(para exportar por ordinal\) sin tener que preocuparse de destrucción de nombre.  
  
```  
#ifdef __cplusplus  
extern "C" {  
#endif  /* __cplusplus */  
  
struct TracerData  
{  
    BOOL    bEnabled;  
    UINT    flags;  
};  
  
BOOL PromptTraceFlags(TracerData FAR* lpData);  
  
#ifdef __cplusplus  
}  
#endif  
```  
  
 Las estructuras utilizadas por la API no se derivan de las clases MFC y se definen en el encabezado de la API.  Esto reduce la complejidad de la interfaz entre el archivo DLL y la aplicación y crea un archivo DLL utilizable por programas de c.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)