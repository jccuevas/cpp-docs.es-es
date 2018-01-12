---
title: "Archivos DLL MFC regular vinculadas dinámicamente a MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 930d56f7bc296225e6fefcf92e49087a2aed99cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>Archivos DLL MFC regular vinculadas dinámicamente a MFC
Normal que MFC DLL vinculado dinámicamente a MFC es un archivo DLL que utiliza MFC internamente y las funciones exportadas en el archivo DLL pueden llamarse desde archivos ejecutables MFC o no MFC. Como se describe en el nombre, este tipo de archivo DLL se compila con la versión de biblioteca de vínculos dinámicos de MFC (conocida también como la versión compartida de MFC). Las funciones se suelen exportar desde DLL de MFC mediante la interfaz estándar de C normal.  
  
 Debe agregar el `AFX_MANAGE_STATE` macro al principio de todas las funciones exportadas en archivos DLL de MFC estándar que se vinculen dinámicamente a MFC para establecer el estado actual del módulo en el otro para el archivo DLL. Esto se realiza agregando la siguiente línea de código al principio de las funciones exportadas desde el archivo DLL:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 Vinculados dinámicamente a MFC normal DLL de MFC, tiene las siguientes características:  
  
-   Se trata de un nuevo tipo de archivo DLL introducido por Visual C++ 4.0.  
  
-   El cliente ejecutable puede escribirse en cualquier lenguaje que admita el uso de archivos DLL (C, C++, Pascal, Visual Basic y así sucesivamente); no tiene que ser una aplicación MFC.  
  
-   A diferencia de la DLL de MFC regular vinculado estáticamente, este tipo de archivo DLL se vincula dinámicamente a la DLL de MFC (también conocido como la DLL compartida de MFC).  
  
-   La biblioteca de importación MFC vinculada a este tipo de archivo DLL es el mismo que se usa para archivos DLL de extensión MFC o las aplicaciones que usan la DLL de MFC: .lib MFCxx (D).  
  
 Vinculados dinámicamente a MFC normal DLL de MFC, tiene los siguientes requisitos:  
  
-   Estos archivos DLL se compilan con **_AFXDLL** definido, como un archivo ejecutable que se vincule dinámicamente a la DLL de MFC. Pero **_USRDLL** también se define como una DLL de MFC normal que se vincula estáticamente a MFC.  
  
-   Debe crear una instancia de este tipo de archivo DLL un `CWinApp`-clase derivada.  
  
-   Este tipo de DLL utiliza la `DllMain` proporcionada por MFC. Coloque todo código de inicialización específico del archivo DLL en el `InitInstance` código de función y la terminación de miembro en `ExitInstance` como en una aplicación MFC normal.  
  
 Dado que este tipo de DLL utiliza la versión de biblioteca de vínculos dinámicos de MFC, debe establecer explícitamente el estado actual del módulo en el otro para el archivo DLL. Para ello, use la [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) macro al principio de cada función exportada desde el archivo DLL.  
  
 archivos DLL de MFC estándar debe tener un `CWinApp`-derivados de clase y un único objeto de esa clase de aplicación, como sucede en una aplicación MFC. Sin embargo, el `CWinApp` objeto de la DLL no tiene un suministro principal de mensajes, como hace el `CWinApp` objeto de una aplicación.  
  
 Tenga en cuenta que el `CWinApp::Run` mecanismo no se aplica a un archivo DLL, porque la aplicación es propietaria del suministro principal de mensajes. Si el archivo DLL muestra cuadros de diálogo no modales o tiene una ventana de marco principal de su propia, el suministro de mensajes principal de la aplicación debe llamar a una rutina exportada por el archivo DLL que llama a `CWinApp::PreTranslateMessage`.  
  
 Colocar toda la inicialización específico del archivo DLL en el `CWinApp::InitInstance` función de miembro como en una aplicación MFC normal. El `CWinApp::ExitInstance` función miembro de la `CWinApp` clase derivada se llama desde la MFC proporcionan `DllMain` función antes de que se descarga el archivo DLL.  
  
 Debe distribuir los archivos DLL compartidos MFCx0.dll y Msvcr*0.dll (o archivos similares) con la aplicación.  
  
 Un archivo DLL que se vincule dinámicamente a MFC no se puede vincular también estáticamente a MFC. Vínculo de aplicaciones para archivos DLL de MFC estándar había vinculado dinámicamente a MFC, al igual que cualquier otro archivo DLL.  
  
 Símbolos se suelen exportar desde DLL de MFC mediante la interfaz estándar de C normal. La declaración de una función exportada desde una DLL de MFC normal es algo parecido a esto:  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 Todas las asignaciones de memoria dentro de una DLL de MFC regular deben permanecer en el archivo DLL; el archivo DLL no debe pasar a o recibir desde el archivo ejecutable de llamada cualquiera de las siguientes acciones:  
  
-   punteros a objetos MFC  
  
-   punteros a la memoria asignada por MFC  
  
 Si necesita realizar cualquiera de los pasos anteriores, o si tiene que pasar objetos derivados de MFC entre el archivo ejecutable de llamada y el archivo DLL, deberá generar un archivo DLL de extensión MFC.  
  
 Es seguro pasar punteros a la memoria que fueron asignados por las bibliotecas de tiempo de ejecución de C entre una aplicación y un archivo DLL solo si se realiza una copia de los datos. No debe eliminar o cambiar el tamaño de estos punteros o utilizarlos sin hacer una copia de la memoria.  
  
 Cuando se vincula una creación de una DLL de MFC normal que dinámicamente a MFC, debe usar la macro [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) para cambiar el estado del módulo MFC correctamente. Esto se realiza agregando la siguiente línea de código al principio de las funciones exportadas desde el archivo DLL:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 El **AFX_MANAGE_STATE** no se debe utilizar la macro en archivos DLL de MFC estándar vinculados estáticamente a MFC ni en archivos DLL de extensión MFC. Para obtener más información, consulte [administrar los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md).  
  
 Para obtener un ejemplo de cómo escribir, crear y usar una DLL normales de MFC, vea el ejemplo [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap). Para obtener más información sobre archivos DLL de MFC estándar que se vinculen dinámicamente a MFC, vea la sección titulada "Convertir DLLScreenCap para dinámicamente vínculo con el archivo DLL de MFC" en el resumen para el ejemplo.  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Inicializar archivos DLL de MFC estándar](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Estados de módulos de una DLL MFC estándar vinculado dinámicamente a MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
  
-   [Administrar los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [Uso de archivos DLL de extensión MFC de base de datos, OLE y Sockets en archivos DLL de MFC estándar](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [Utilizar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
## <a name="see-also"></a>Vea también  
 [Tipos de archivos DLL](../build/kinds-of-dlls.md)