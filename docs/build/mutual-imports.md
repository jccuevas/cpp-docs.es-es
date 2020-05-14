---
title: Importaciones mutuas
ms.date: 11/04/2016
helpviewer_keywords:
- mutual DLL imports [C++]
- AFX_DATA
- importing DLLs [C++], mutual imports
- mutually importing executable files [C++]
- AFX_EXT_CLASS macro
- circular imports
- _AFXEXT preprocessor symbol
- DLLs [C++], importing
- executable files [C++], importing
- extension DLLs [C++], mutual imports
- exporting DLLs [C++], mutual imports
ms.assetid: 2cc29537-92ee-4d92-af39-8b8b3afd808f
ms.openlocfilehash: f01e69138a6ca1744645a1c2fa8525b7088e260d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295682"
---
# <a name="mutual-imports"></a>Importaciones mutuas

La exportación o importación a otro archivo ejecutable presenta complicaciones cuando las importaciones son mutuas (o circulares). Por ejemplo, dos archivos DLL importan símbolos entre sí, de forma similar a las funciones mutuamente recursivas.

El problema con la importación mutua de archivos ejecutables (normalmente DLL) es que uno no se puede compilar sin compilar primero el otro. Cada proceso de compilación requiere, como entrada, una biblioteca de importación generada por el otro proceso de compilación.

La solución consiste en usar la utilidad LIB con la opción /DEF, que genera una biblioteca de importación sin compilar el archivo ejecutable. Con esta utilidad, puede compilar todas las bibliotecas de importación que necesite, con independencia de cuántos archivos DLL estén implicados o de la complejidad de las dependencias.

La solución general para controlar las importaciones mutuas consiste en:

1. Tomar cada DLL de forma individual. (Se permite cualquier orden, aunque algunos son más óptimos). Si todas las bibliotecas de importación necesarias existen y están actualizadas, ejecute LINK para compilar el archivo ejecutable (DLL). Esto genera una biblioteca de importación. De lo contrario, ejecute LIB para generar una biblioteca de importación.

   Al ejecutar LIB con la opción /DEF se genera un archivo adicional con una extensión .EXP. El archivo .EXP se debe usar después para compilar el archivo ejecutable.

1. Después de usar LINK o LIB para compilar todas las bibliotecas de importación, vuelva y ejecute LINK para compilar los archivos ejecutables que no se hayan compilado en el paso anterior. Tenga en cuenta que en la línea de LINK se debe especificar el archivo .exp correspondiente.

   Si antes hubiera ejecutado la utilidad LIB para generar una biblioteca de importación para DLL1, LIB también habría generado el archivo DLL1.exp. Tendrá que usar DLL1.exp como entrada para LINK al compilar DLL1.dlll.

En la ilustración siguiente se muestra una solución para dos DLL de importación mutua, DLL1 y DLL2. El paso 1 consiste en ejecutar LIB, con la opción /DEF establecida, en DLL1. El paso 1 genera DLL1.lib (una biblioteca de importación) y DLL1.exp. En el paso 2, se usa la biblioteca de importación para crear DLL2 que, a su vez, genera una biblioteca de importación para los símbolos de DLL2. En el paso 3 se crea DLL1, con DLL1.exp y DLL2.lib como entrada. Tenga en cuenta que no se necesita un archivo .exp para DLL2, porque no se ha usado LIB para compilar la biblioteca de importación de DLL2.

![Using mutual imports to link two DLLs](media/vc37yj1.gif "Uso de importaciones mutuas para vincular dos archivos DLL")<br/>
Vincular dos archivos DLL con importaciones mutuas

## <a name="limitations-of-_afxext"></a>Limitaciones de _AFXEXT

Puede usar el símbolo de preprocesador `_AFXEXT` para los archivos DLL de extensión de MFC, siempre y cuando no disponga de varios niveles de ellos. Si tiene archivos DLL de extensión de MFC que llaman o se derivan de clases de archivos DLL de extensión de MFC propios, que a su vez se derivan de las clases MFC, tendrá que usar un símbolo de preprocesador propio para evitar ambigüedades.

El problema es que, en Win32, debe declarar de forma explícita cualquier dato como **__declspec(dllexport)** si se va a exportar desde un archivo DLL y como **__declspec(dllimport)** si se va a importar desde un archivo DLL. Al definir `_AFXEXT`, los encabezados de MFC garantizan que **AFX_EXT_CLASS** se defina correctamente.

Cuando hay varias capas, un símbolo como **AFX_EXT_CLASS** no es suficiente, porque es posible que un archivo DLL de extensión de MFC exporte nuevas clases e importe otras desde otro archivo DLL de extensión de MFC. Para solucionar este problema, use un símbolo de preprocesador especial que indique que se va a compilar el propio archivo DLL, no a usarlo. Por ejemplo, imagine dos archivo DLL de extensión de MFC, A.dll y B.dll. Cada uno exporta algunas clases de A.h y B.h, respectivamente. B.dll usa las clases de A.dll. Los archivos de encabezado serían similares a los siguientes:

```
/* A.H */
#ifdef A_IMPL
   #define CLASS_DECL_A   __declspec(dllexport)
#else
   #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ ... class definition ... };

// B.H
#ifdef B_IMPL
   #define CLASS_DECL_B   __declspec(dllexport)
#else
   #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ ... class definition ... };
...
```

Cuando se compila A.dll, lo hace con `/D A_IMPL` y, cuando se compila B.dll, lo hace con `/D B_IMPL`. Al usar símbolos independientes para cada archivo DLL, al compilar B.dll se exporta `CExampleB` y se importa `CExampleA`. `CExampleA` se exporta al compilar A.dll y se importa cuando lo usa B.dll (u otro cliente).

Este tipo de distribución en capas no se puede realizar cuando se usa la instancia integrada de **AFX_EXT_CLASS** y los símbolos de preprocesador `_AFXEXT`. La técnica descrita antes soluciona este problema de manera similar al mecanismo que usa MFC para compilar sus archivos DLL de extensión MFC de red, base de datos y tecnologías activas.

## <a name="not-exporting-the-entire-class"></a>No se exporta la clase completa

Cuando no se exporta una clase completa, es necesario asegurarse de que los elementos de datos necesarios creados por las macros de MFC se exporten correctamente. Para ello, se puede volver a definir `AFX_DATA` en la macro de la clase específica. Esto se debe hacer siempre que no se exporte toda la clase.

Por ejemplo:

```
/* A.H */
#ifdef A_IMPL
   #define CLASS_DECL_A  _declspec(dllexport)
#else
   #define CLASS_DECL_A  _declspec(dllimport)
#endif

#undef  AFX_DATA
#define AFX_DATA CLASS_DECL_A

class CExampleA : public CObject
{
   DECLARE_DYNAMIC()
   CLASS_DECL_A int SomeFunction();
   //... class definition ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportación desde un archivo DLL](exporting-from-a-dll.md)

- [Exportación desde un archivo DLL mediante archivos .DEF](exporting-from-a-dll-using-def-files.md)

- [Exportación desde un archivo DLL mediante __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportación e importación mediante AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportación de funciones de C++ para usarlas en ejecutables del lenguaje C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Determinación del método de exportación que se va a usar](determining-which-exporting-method-to-use.md)

- [Importación a una aplicación mediante __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [La utilidad LIB y la opción /DEF](reference/lib-reference.md)

## <a name="see-also"></a>Vea también

[Importar y exportar](importing-and-exporting.md)
