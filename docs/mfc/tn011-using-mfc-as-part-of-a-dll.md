---
title: 'TN011: Utilizar MFC como parte de un archivo DLL'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.dll
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
ms.openlocfilehash: 7e9fda44e2af4ec32bae6299fbcc0eda17984f9b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306255"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011: Utilizar MFC como parte de un archivo DLL

Esta nota describe los archivos DLL de MFC estándar, que le permiten utilizar la biblioteca MFC como parte de una biblioteca de vínculos dinámicos (DLL) de Windows. Se supone que está familiarizado con los archivos DLL de Windows y cómo crearlas. Para obtener información acerca de los archivos DLL de extensión de MFC, con lo que puede crear extensiones a la biblioteca MFC, vea [versión de DLL de MFC](../mfc/tn033-dll-version-of-mfc.md).

## <a name="dll-interfaces"></a>Interfaces DLL

archivos DLL de MFC estándar suponen interfaces entre la aplicación y el archivo DLL se especifican en el tipo C de funciones o clases exportadas explícitamente. No se puede exportar las interfaces de clases MFC.

Si un archivo DLL y una aplicación desean usar MFC, ambos tienen una opción para usar la versión compartida de las bibliotecas MFC o para vincular estáticamente a una copia de las bibliotecas. La aplicación y DLL pueden utilizar una de las versiones estándares de la biblioteca MFC.

archivos DLL de MFC estándar tiene varias ventajas:

- La aplicación que utiliza el archivo DLL no tiene que utilizar MFC y no tiene que ser una aplicación de Visual C++.

- Con MFC archivos DLL estándar vinculados estáticamente a MFC, el tamaño del archivo DLL depende solo las rutinas en tiempo de ejecución MFC y C que se usan y vinculadas.

- Con la DLL de MFC normal que se vinculan dinámicamente a MFC, el ahorro de memoria del uso de la versión compartida de MFC puede ser significativo. Sin embargo, debe distribuir los archivos DLL compartidos, Mfc\<*versión*> .dll y Msvvcrt\<*versión*> .dll con el archivo DLL.

- El diseño del archivo DLL depende de cómo se implementan las clases. El diseño de la DLL exporta solo a las API que desee. Como resultado, si cambia la implementación, los archivos DLL estándar de MFC siguen siendo válidas.

- Con archivos DLL de MFC estándar vinculados estáticamente a MFC, si el archivo DLL y aplicación utilizan MFC, no hay ningún problema con la aplicación que desea que una versión diferente de MFC que el archivo DLL o viceversa. Dado que la biblioteca MFC se vincula estáticamente en cada archivo DLL o EXE, no hay ninguna pregunta sobre qué versión tiene.

## <a name="api-limitations"></a>Limitaciones de API

Algunas funciones MFC no es aplicable a la versión DLL, ya sea debido a limitaciones técnicas o porque esos servicios se proporcionan normalmente por la aplicación. Con la versión actual de MFC, es la única función que no es aplicable `CWinApp::SetDialogBkColor`.

## <a name="building-your-dll"></a>Compilar el archivo DLL

Al compilar archivos DLL de MFC estándar vinculados estáticamente a MFC, los símbolos `_USRDLL` y `_WINDLL` debe definirse. El código del archivo DLL también debe compilarse con los siguientes modificadores del compilador:

- **/ D_WINDLL** significa que la compilación es para un archivo DLL

- **/ D_USRDLL** especifica la creación de un archivo DLL MFC

También debe definir estos símbolos y usar estos modificadores de compilador al compilar archivos DLL de MFC estándar vinculados dinámicamente a MFC. Además, el símbolo `_AFXDLL` deben definirse y el código del archivo DLL debe compilarse con:

- **/ D_AFXDLL** especifica que se está creando una DLL de MFC normal que se vincule dinámicamente a MFC

Las interfaces (API) entre la aplicación y el archivo DLL deben exportarse explícitamente. Se recomienda que defina las interfaces para que sea el ancho de banda bajo y usar interfaces de C solo si es posible. Interfaces C directas son más fáciles de mantener que las clases de C++ más complejas.

Coloque sus API en un encabezado independiente que se puede incluir archivos de C y C++. Vea el encabezado ScreenCap.h en el ejemplo de conceptos avanzados de MFC [DLLScreenCap](../overview/visual-cpp-samples.md) para obtener un ejemplo. Para exportar las funciones, escríbalos en el `EXPORTS` sección del archivo de definición de módulo (. DEF) o incluir `__declspec(dllexport)` en sus definiciones de función. Use `__declspec(dllimport)` para importar estas funciones en el archivo ejecutable del cliente.

Debe agregar la macro AFX_MANAGE_STATE al principio de todas las funciones exportadas en archivos DLL de MFC estándar vinculados dinámicamente a MFC. Esta macro establece el estado actual del módulo en el otro para el archivo DLL. Para usar esta macro, agregue la siguiente línea de código al principio de las funciones exportadas desde el archivo DLL:

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>WinMain -> DllMain

La biblioteca MFC define el estándar de Win32 `DllMain` punto de entrada que inicializa la [CWinApp](../mfc/reference/cwinapp-class.md) derivado como en una aplicación típica de MFC. Colocar toda la inicialización específica para DLL en el [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) método como en una aplicación típica de MFC.

Tenga en cuenta que el [CWinApp:: Run](../mfc/reference/cwinapp-class.md#run) mecanismo no se aplica a un archivo DLL, porque la aplicación es propietaria del suministro de mensajes principal. Si el archivo DLL muestra cuadros de diálogo no modales o tiene una ventana de marco principal de su propio, el bombeo de mensajes principal de la aplicación debe llamar a una rutina exportada por el archivo DLL que llama a [CWinApp:: PreTranslateMessage](../mfc/reference/cwinapp-class.md#pretranslatemessage).

Vea el ejemplo DLLScreenCap para su uso de esta función.

El `DllMain` función que MFC proporciona llamará el [CWinApp:: ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) método de la clase que se deriva de `CWinApp` antes de descargar el archivo DLL.

## <a name="linking-your-dll"></a>Vinculación del archivo DLL

Con MFC archivos DLL estándar vinculados estáticamente a MFC, debe vincular el archivo DLL con Nafxcwd.lib o Nafxcw.lib y con la versión de los tiempos de ejecución de C denominado Libcmt.lib. Estas bibliotecas son pregeneradas y pueden instalarse mediante la especificación de ellas al ejecutar el programa de instalación de Visual C++.

## <a name="sample-code"></a>Código de ejemplo

Vea el ejemplo de conceptos avanzados de programa DLLScreenCap para obtener un ejemplo completo. Varios puntos interesantes que tener en cuenta en este ejemplo es los siguientes:

- Las marcas de compilador de la DLL y los de la aplicación son diferentes.

- Las líneas de vínculo y. DEF (archivos) para el archivo DLL y los de la aplicación son diferentes.

- La aplicación que utiliza el archivo DLL no tiene que estar en C++.

- La interfaz entre la aplicación y el archivo DLL es una API que se puede usar por C o C++ y se exporta con DLLScreenCap.def.

El ejemplo siguiente ilustra una API que se define en normal DLL de MFC que se vincule estáticamente a MFC. En este ejemplo, la declaración está incluida en un `extern "C" { }` bloque para los usuarios de C++. Esto tiene varias ventajas. En primer lugar, hace las API de DLL puede usar las aplicaciones cliente que no son de C++. En segundo lugar, reduce la sobrecarga DLL ya C++ daños en los nombres no se aplicará el nombre exportado. Por último, resulta más fácil agregar explícitamente a una. Archivo DEF (para exportar por ordinal) sin tener que preocuparse por daños en los nombres.

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

Las estructuras utilizadas por la API no se derivan las clases MFC y se definen en el encabezado de la API. Esto reduce la complejidad de la interfaz entre el archivo DLL y la aplicación y hace que el archivo DLL puede usar programas de C.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
