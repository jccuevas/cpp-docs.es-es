---
title: 'TN011: Usar MFC como parte de un archivo DLL | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.dll
dev_langs:
- C++
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d0ac05e314f3f8354ba289695afa672b1e28881
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011: Usar MFC como parte de un archivo DLL
Esta nota describe archivos DLL de MFC estándar, que le permiten utilizar la biblioteca MFC como parte de una biblioteca de vínculos dinámicos (DLL) de Windows. Se supone que está familiarizado con los archivos DLL de Windows y cómo crearlos. Para obtener información sobre archivos DLL de extensión MFC, con lo que puede crear extensiones a la biblioteca MFC, vea [versión de DLL de MFC](../mfc/tn033-dll-version-of-mfc.md).  
  
## <a name="dll-interfaces"></a>Interfaces DLL  
 archivos DLL de MFC estándar supone interfaces entre la aplicación y el archivo DLL se especifican en las funciones de tipo C o clases exportadas explícitamente. No se puede exportar las interfaces de clase MFC.  
  
 Si un archivo DLL y una aplicación desean usar MFC, tienen una opción para usar la versión compartida de MFC (bibliotecas) o para vincular estáticamente a una copia de las bibliotecas. La aplicación y el archivo DLL pueden utilizar una de las versiones estándares de la biblioteca MFC.  
  
 archivos DLL de MFC estándar tiene varias ventajas:  
  
-   La aplicación que utiliza el archivo DLL no tiene que usar MFC y no tiene que ser una aplicación de Visual C++.  
  
-   Con MFC archivos DLL estándar vinculados estáticamente a MFC, el tamaño del archivo DLL depende solo para las rutinas en tiempo de ejecución de C y MFC que se usan y se vincula.  
  
-   Con las DLL de MFC normal que se vinculen dinámicamente a MFC, el ahorro de memoria derivado de utilizar la versión compartida de MFC puede ser importante. Sin embargo, debe distribuir los archivos DLL compartidos, Mfc*\<versión >*.dll y Msvvcrt*\<versión >*.dll, con el archivo DLL.  
  
-   El diseño del archivo DLL es independiente de cómo se implementan las clases. El diseño de la DLL exporta solo a las API que desee. Como resultado, si cambia la implementación, archivos DLL estándar de MFC siguen siendo válidas.  
  
-   Con archivos DLL de MFC estándar vinculados estáticamente a MFC, si el archivo DLL y aplicación utilizan MFC, no hay ningún problema con la aplicación que desea que una versión diferente de MFC que el archivo DLL o viceversa. Dado que la biblioteca MFC está vinculada estáticamente en cada archivo DLL o EXE, no hay ninguna pregunta sobre a qué versión tiene.  
  
## <a name="api-limitations"></a>Limitaciones de la API  
 Algunas funciones MFC no se aplican a la versión del archivo DLL, ya sea debido a las limitaciones técnicas o porque esos servicios normalmente se proporcionan con la aplicación. Con la versión actual de MFC, es la única función que no es aplicable a `CWinApp::SetDialogBkColor`.  
  
## <a name="building-your-dll"></a>Generar el archivo DLL  
 Al compilar los archivos DLL de MFC estándar vinculados estáticamente a MFC, los símbolos `_USRDLL` y `_WINDLL` deben definirse. El código del archivo DLL también debe compilarse con los modificadores de compilador siguientes:  
  
- **/ D_WINDLL** significa que la compilación es para un archivo DLL  
  
- **/ D_USRDLL** especifica la generación de una DLL de MFC normal  
  
 También debe definir estos símbolos y utilizar estos modificadores del compilador al compilar archivos DLL de MFC estándar que se vinculen dinámicamente a MFC. Además, el símbolo `_AFXDLL` debe definirse y el código del archivo DLL debe compilarse con:  
  
- **/ D_AFXDLL** especifica que se está creando una DLL de MFC normal que se vincula dinámicamente a MFC  
  
 Las interfaces (API) entre la aplicación y el archivo DLL deben exportarse explícitamente. Se recomienda que define las interfaces para que sea poco ancho de banda y usar interfaces de C solo si es posible. Interfaces de C directas son más fáciles de mantener que las clases de C++ más complejas.  
  
 Coloque las API en un encabezado independiente que se pueden incluir archivos de C y C++. Vea el encabezado ScreenCap.h en el ejemplo de conceptos avanzados de MFC [DLLScreenCap](../visual-cpp-samples.md) para obtener un ejemplo. Para exportar las funciones, escribirlos en la `EXPORTS` sección de su archivo de definición de módulo (. DEF) o incluir `__declspec(dllexport)` en sus definiciones de función. Use `__declspec(dllimport)` para importar estas funciones en la aplicación cliente.  
  
 Debe agregar el `AFX_MANAGE_STATE` macro al principio de todas las funciones exportadas en archivos DLL de MFC estándar que se vinculen dinámicamente a MFC. Esta macro establece el estado actual del módulo en el otro para el archivo DLL. Para usar esta macro, agregue la siguiente línea de código al principio de las funciones exportadas desde el archivo DLL:  
  
 `AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`  
  
## <a name="winmain---dllmain"></a>WinMain -> DllMain  
 La biblioteca MFC define el estándar de Win32 `DllMain` punto de entrada que inicializa el [CWinApp](../mfc/reference/cwinapp-class.md) objeto como en una aplicación MFC típica derivado. Colocar toda la inicialización específico del archivo DLL en el [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) método como en una aplicación típica de MFC.  
  
 Tenga en cuenta que la [CWinApp:: Run](../mfc/reference/cwinapp-class.md#run) mecanismo no se aplica a un archivo DLL, porque la aplicación es propietaria del suministro principal de mensajes. Si el archivo DLL muestra cuadros de diálogo no modales o tiene una ventana de marco principal de su propia, el suministro de mensajes principal de la aplicación debe llamar a una rutina exportada por el archivo DLL que llama [CWinApp:: PreTranslateMessage](../mfc/reference/cwinapp-class.md#pretranslatemessage).  
  
 Vea el ejemplo DLLScreenCap para el uso de esta función.  
  
 El `DllMain` función que MFC proporciona llamará el [CWinApp:: ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) método de la clase que se deriva de `CWinApp` antes de que se descarga el archivo DLL.  
  
## <a name="linking-your-dll"></a>Vincular al archivo DLL  
 Con MFC archivos DLL estándar vinculados estáticamente a MFC, debe vincularse al archivo DLL Nafxcwd.lib o Nafxcw.lib y a la versión de los tiempos de ejecución de C denominado Libcmt.lib. Estas bibliotecas se compilan previamente y pueden instalarse mediante la especificación de cuando se ejecuta el programa de instalación de Visual C++.  
  
## <a name="sample-code"></a>Código de ejemplo  
 Vea el ejemplo de conceptos avanzados de MFC programa DLLScreenCap para obtener un ejemplo completo. Varios aspectos interesantes que se tenga en cuenta en este ejemplo son los siguientes:  
  
-   Los marcadores del compilador de la DLL y los de la aplicación son diferentes.  
  
-   Las líneas de vínculo y. DEF (archivos) para el archivo DLL y los de la aplicación son diferentes.  
  
-   La aplicación que utiliza el archivo DLL no tiene en C++.  
  
-   La interfaz entre la aplicación y el archivo DLL es una API que puede usar C o C++ y se exporta con DLLScreenCap.def.  
  
 En el ejemplo siguiente se muestra una API que se define en normal DLL de MFC que se vincula estáticamente a MFC. En este ejemplo, la declaración se incluye en un `extern "C" { }` bloque para los usuarios de C++. Esto tiene varias ventajas. En primer lugar, realiza las API de archivo DLL utilizable por las aplicaciones cliente no de C++. En segundo lugar, reduce la sobrecarga de DLL porque la eliminación de nombres de C++ no se aplicará el nombre exportado. Por último, es más fácil agregar explícitamente a una. Archivo DEF (para exportar por ordinal) sin tener que preocuparse sobre la eliminación de nombres.  
  
```  
#ifdef __cplusplus  
extern "C" {  
#endif  /* __cplusplus */  
 
struct TracerData  
{  
    BOOL bEnabled;  
    UINT flags;  
};  
 
BOOL PromptTraceFlags(TracerData FAR* lpData);

 
#ifdef __cplusplus  
}  
#endif  
```  
  
 Las estructuras utilizadas por la API no se derivan de clases de MFC y se definen en el encabezado de la API. Esto reduce la complejidad de la interfaz entre el archivo DLL y la aplicación y hace que el archivo DLL puede usar programas de C.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

