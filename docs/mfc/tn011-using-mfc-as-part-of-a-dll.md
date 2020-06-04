---
title: 'TN011: Usar MFC como parte de un archivo DLL'
ms.date: 11/04/2016
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
ms.openlocfilehash: 0f4d4e2ed76a0fa5f8f775345fc672a1df055a39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370435"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011: Usar MFC como parte de un archivo DLL

Esta nota describe los archivos DLL de MFC normales, que permiten usar la biblioteca MFC como parte de una biblioteca de vínculos dinámicos (DLL) de Windows. Se supone que está familiarizado con los archivos DLL de Windows y cómo compilarlos. Para obtener información acerca de los archivos DLL de extensión MFC, con los que puede crear extensiones para la biblioteca MFC, vea [Versión DLL de MFC](../mfc/tn033-dll-version-of-mfc.md).

## <a name="dll-interfaces"></a>DLL Interfaces

Los archivos DLL de MFC normales suponen que las interfaces entre la aplicación y el archivo DLL se especifican en funciones de tipo C o clases exportadas explícitamente. Las interfaces de clase MFC no se pueden exportar.

Si un archivo DLL y una aplicación desean usar MFC, ambos tienen la opción de usar la versión compartida de las bibliotecas MFC o vincular estáticamente a una copia de las bibliotecas. La aplicación y el archivo DLL pueden usar una de las versiones estándar de la biblioteca MFC.

LOS archivos DLL de MFC normales tienen varias ventajas:

- La aplicación que usa el archivo DLL no tiene que usar MFC y no tiene que ser una aplicación de Visual C++.

- Con archivos DLL de MFC normales que se vinculan estáticamente a MFC, el tamaño del archivo DLL depende solo de las rutinas de tiempo de ejecución de MFC y C que se usan y vinculan.

- Con los archivos DLL de MFC normales que se vinculan dinámicamente a MFC, el ahorro en memoria por el uso de la versión compartida de MFC puede ser significativo. Sin embargo, debe distribuir los\<archivos DLL compartidos, la\<*versión* de Mfc>.dll y msvvcrt*versión*>.dll, con el archivo DLL.

- El diseño de DLL es independiente de cómo se implementan las clases. El diseño de DLL solo se exporta a las API que desee. Como resultado, si cambia la implementación, los archivos DLL de MFC normales siguen siendo válidos.

- Con archivos DLL de MFC normales que se vinculan estáticamente a MFC, si DLL y aplicación usan MFC, no hay problemas con la aplicación que desea una versión diferente de MFC que el archivo DLL o viceversa. Dado que la biblioteca MFC está vinculada estáticamente a cada dll o EXE, no hay ninguna duda acerca de qué versión tiene.

## <a name="api-limitations"></a>Limitaciones de API

Algunas funciones de MFC no se aplican a la versión DLL, ya sea debido a limitaciones técnicas o porque la aplicación suele proporcionar esos servicios. Con la versión actual de MFC, la `CWinApp::SetDialogBkColor`única función que no es aplicable es .

## <a name="building-your-dll"></a>Creación de su DLL

Al compilar archivos DLL de MFC normales que se `_USRDLL` `_WINDLL` vinculan estáticamente a MFC, los símbolos y deben definirse. El código DLL también debe compilarse con los siguientes modificadores del compilador:

- **/D_WINDLL** significa que la compilación es para un archivo DLL

- **/D_USRDLL** especifica que está creando un archivo DLL de MFC normal

También debe definir estos símbolos y usar estos modificadores del compilador al compilar archivos DLL de MFC normales que se vinculan dinámicamente a MFC. Además, `_AFXDLL` el símbolo debe definirse y el código DLL debe compilarse con:

- **/D_AFXDLL** especifica que está creando un archivo DLL de MFC normal que se vincula dinámicamente a MFC

Las interfaces (API) entre la aplicación y el archivo DLL deben exportarse explícitamente. Le recomendamos que defina sus interfaces para que sean de ancho de banda bajo y utilice solo interfaces C si puede. Las interfaces C directas son más fáciles de mantener que las clases C++ más complejas.

Coloque las API en un encabezado independiente que pueda incluir los archivos C y C++. Vea el encabezado ScreenCap.h en el ejemplo [DLLScreenCap](../overview/visual-cpp-samples.md) de conceptos avanzados de MFC para obtener un ejemplo. Para exportar las funciones, `EXPORTS` introdúzcalas en la sección del archivo de definición del módulo (. DEF) o `__declspec(dllexport)` incluir en las definiciones de función. Se `__declspec(dllimport)` utiliza para importar estas funciones en el ejecutable del cliente.

Debe agregar la macro AFX_MANAGE_STATE al principio de todas las funciones exportadas en archivos DLL de MFC normales que se vinculan dinámicamente a MFC. Esta macro establece el estado actual del módulo en el del archivo DLL. Para utilizar esta macro, agregue la siguiente línea de código al principio de las funciones exportadas desde el archivo DLL:

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>WinMain -> DllMain

La biblioteca MFC define el `DllMain` punto de entrada Win32 estándar que inicializa el objeto derivado [de CWinApp](../mfc/reference/cwinapp-class.md) como en una aplicación MFC típica. Coloque toda la inicialización específica de DLL en el método [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) como en una aplicación MFC típica.

Tenga en cuenta que el mecanismo [CWinApp::Run](../mfc/reference/cwinapp-class.md#run) no se aplica a un archivo DLL, porque la aplicación es propietaria de la bomba de mensajes principal. Si el archivo DLL muestra cuadros de diálogo no iniciados o tiene una ventana de marco principal propia, la bomba de mensajes principal de la aplicación debe llamar a una rutina exportada por DLL que llame a [CWinApp::PreTranslateMessage](../mfc/reference/cwinapp-class.md#pretranslatemessage).

Consulte el ejemplo DLLScreenCap para obtener el uso de esta función.

La `DllMain` función que proporciona MFC llamará al método [CWinApp::ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) de la clase que se deriva antes `CWinApp` de descargar el archivo DLL.

## <a name="linking-your-dll"></a>Vinculación de su archivo DLL

Con los archivos DLL de MFC normales que se vinculan estáticamente a MFC, debe vincular el archivo DLL con Nafxcwd.lib o Nafxcw.lib y con la versión de los tiempos de ejecución de C denominada Libcmt.lib. Estas bibliotecas están precompiladas y se pueden instalar especificándolas al ejecutar la instalación de Visual C++.

## <a name="sample-code"></a>Código de ejemplo

Consulte el programa de ejemplo Conceptos avanzados de MFC DLLScreenCap para obtener un ejemplo completo. Varias cosas interesantes a tener en cuenta en este ejemplo son las siguientes:

- Los indicadores del compilador del archivo DLL y los de la aplicación son diferentes.

- Las líneas de enlace y . LOS archivos DEF para el archivo DLL y los de la aplicación son diferentes.

- La aplicación que utiliza el archivo DLL no tiene que estar en C++.

- La interfaz entre la aplicación y el archivo DLL es una API que c o C++ puede usar y se exporta con DLLScreenCap.def.

En el ejemplo siguiente se muestra una API que se define en un archivo DLL de MFC normal que se vincula estáticamente a MFC. En este ejemplo, la declaración `extern "C" { }` se incluye en un bloque para los usuarios de C++. Esto tiene varias ventajas. En primer lugar, hace que las API de DLL puedan ser utilizables por aplicaciones cliente que no sean De C++. En segundo lugar, reduce la sobrecarga de DLL porque la manipulación de nombres C++ no se aplicará al nombre exportado. Por último, facilita la adición explícita a un archivo . DEF (para exportar por ordinal) sin tener que preocuparse por el mangling de nombres.

```cpp
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

Las estructuras utilizadas por la API no se derivan de clases MFC y se definen en el encabezado de la API. Esto reduce la complejidad de la interfaz entre el archivo DLL y la aplicación y hace que el archivo DLL sea utilizable por los programas C.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
