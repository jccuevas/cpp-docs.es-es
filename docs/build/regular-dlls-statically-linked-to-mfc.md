---
title: "Archivos DLL MFC regular vinculadas estáticamente a MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ef25785e3d1e37ee622572f03fce56b1fa236aa
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2018
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>Archivos DLL MFC regular vinculadas estáticamente a MFC
Normal que MFC DLL vinculado estáticamente a MFC es un archivo DLL que utiliza MFC internamente y las funciones exportadas en el archivo DLL pueden llamarse desde archivos ejecutables MFC o no MFC. Como se describe en el nombre, este tipo de archivo DLL se compila con la versión de biblioteca de vínculos estáticos de MFC. Las funciones se suelen exportar desde DLL de MFC mediante la interfaz estándar de C normal. Para obtener un ejemplo de cómo escribir, crear y usar una DLL normales de MFC, vea el ejemplo [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap).  
  
 Tenga en cuenta que el término USRDLL ya no se usa en la documentación de Visual C++. Una DLL de MFC normal que se vincula estáticamente a MFC tiene las mismas características que el antiguo archivo USRDLL.  
  
 Una DLL de MFC normales, vinculados estáticamente a MFC, tiene las siguientes características:  
  
-   El cliente ejecutable puede escribirse en cualquier lenguaje que admita el uso de archivos DLL (C, C++, Pascal, Visual Basic y así sucesivamente); no tiene que ser una aplicación MFC.  
  
-   El archivo DLL puede vincular a las mismas bibliotecas de vínculos estáticos de MFC usadas las aplicaciones. Ya no es una versión independiente de las bibliotecas de vínculos estáticos para archivos DLL.  
  
-   Antes de la versión 4.0 de MFC, los archivos USRDLL proporcionaban el mismo tipo de funcionalidad como archivos DLL de MFC estándar vinculados estáticamente a MFC. A partir de Visual C++ versión 4.0, el término USRDLL está obsoleta.  
  
 Una DLL de MFC normales, vinculados estáticamente a MFC, tiene los siguientes requisitos:  
  
-   Este tipo de archivo DLL debe crear una instancia de una clase derivada de `CWinApp`.  
  
-   Este tipo de DLL utiliza la `DllMain` proporcionada por MFC. Coloque todo código de inicialización específico del archivo DLL en el `InitInstance` código de función y la terminación de miembro en `ExitInstance` como en una aplicación MFC normal.  
  
-   Aunque el término USRDLL está obsoleto, todavía tendrá que definir "**_USRDLL**" en la línea de comandos del compilador. Esta definición determina las declaraciones que se extraigan de los archivos de encabezado MFC.  
  
 archivos DLL de MFC estándar debe tener un `CWinApp`-derivados de clase y un único objeto de esa clase de aplicación, como sucede en una aplicación MFC. Sin embargo, el `CWinApp` objeto de la DLL no tiene un suministro principal de mensajes, como hace el `CWinApp` objeto de una aplicación.  
  
 Tenga en cuenta que el `CWinApp::Run` mecanismo no se aplica a un archivo DLL, porque la aplicación es propietaria del suministro principal de mensajes. Si el archivo DLL abre los cuadros de diálogo no modales o tiene una ventana de marco principal de su propia, el suministro de mensajes principal de la aplicación debe llamar a una rutina exportada por el archivo DLL que llama a su vez el `CWinApp::PreTranslateMessage` función miembro de objeto de aplicación de los archivos DLL.  
  
 Para obtener un ejemplo de esta función, vea el ejemplo DLLScreenCap.  
  
 Símbolos se suelen exportar desde DLL de MFC mediante la interfaz estándar de C normal. La declaración de una función exportada desde una DLL de MFC normal sería algo parecido a esto:  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 Todas las asignaciones de memoria dentro de una DLL de MFC regular deben permanecer en el archivo DLL; el archivo DLL no debe pasar a o recibir desde el archivo ejecutable de llamada cualquiera de las siguientes acciones:  
  
-   punteros a objetos MFC  
  
-   punteros a la memoria asignada por MFC  
  
 Si necesita realizar cualquiera de los pasos anteriores o necesita pasar objetos derivados de MFC entre el archivo ejecutable de llamada y el archivo DLL, deberá generar un archivo DLL de extensión MFC.  
  
 Es seguro pasar punteros a la memoria que fueron asignados por las bibliotecas de tiempo de ejecución de C entre una aplicación y un archivo DLL solo si se realiza una copia de los datos. No debe eliminar o cambiar el tamaño de estos punteros o utilizarlos sin hacer una copia de la memoria.  
  
 Un archivo DLL que está vinculado estáticamente a MFC también dinámicamente no se puede vincular a los archivos DLL de MFC compartida. Un archivo DLL que está vinculado estáticamente a MFC se enlaza dinámicamente a una aplicación igual que cualquier otro archivo DLL; las aplicaciones que se vinculan a él al igual que cualquier otro archivo DLL.  
  
 Las bibliotecas de vínculos estáticos de MFC estándar se denominan según la convención descrita en [convenciones de nomenclatura para archivos DLL de MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Sin embargo, con la versión 3.0 y versiones posterior de MFC, ya no es necesario especificar manualmente al vinculador la versión de la biblioteca MFC que desea vincular en. En su lugar, los archivos de encabezado MFC determinan automáticamente la versión correcta de la biblioteca MFC debe vincular en preprocesador según define, como  **\_depurar** o **_UNICODE**. Los archivos de encabezado MFC agregan directivas de DEFAULTLIB indica al vinculador que debe vincular una versión específica de la biblioteca MFC.  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Inicializar archivos DLL de MFC estándar](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Utilizar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [Uso de archivos DLL de extensión MFC de base de datos, OLE y Sockets en archivos DLL de MFC estándar](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [Crear un archivo DLL de MFC](../mfc/reference/mfc-dll-wizard.md)  
  
-   [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Archivos DLL de extensión MFC](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>Vea también  
 [Tipos de archivos DLL](../build/kinds-of-dlls.md)