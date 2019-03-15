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
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814558"
---
# <a name="mutual-imports"></a>Importaciones mutuas

Exportar o importar a otro archivo ejecutable presenta complicaciones cuando las importaciones mutuas (o circulares). Por ejemplo, dos archivos DLL importa símbolos entre sí, similar a las funciones mutuamente recursivas.

El problema de importar mutuamente archivos ejecutables (generalmente dll) es que no se puede compilar sin tener que crear la primera de otra. Cada proceso de compilación requiere, como entrada, una biblioteca de importación generada por el otro proceso de compilación.

La solución es usar la utilidad LIB con la opción /DEF, que genera una biblioteca de importación sin tener que crear el archivo ejecutable. Con esta utilidad, puede crear todas las bibliotecas de importación que necesita, independientemente de cuántos archivos DLL haya implicados y cómo complejidad de las dependencias.

La solución general para el tratamiento de importaciones mutuas es:

1. Tener a su vez cada DLL. (Cualquier orden es factible, aunque resultan más óptimos algunos pedidos). Si todas las bibliotecas de importación necesarias existen y están actualizadas, ejecute LINK para generar el archivo ejecutable (DLL). Esto genera una biblioteca de importación. En caso contrario, ejecute LIB para generar una biblioteca de importación.

   Ejecutar LIB con la opción /DEF genera un archivo adicional con un. Extensión EXP. El archivo. Archivo EXP debe usarse posteriormente para generar el archivo ejecutable.

1. Después de usar el vínculo o LIB para generar todas las bibliotecas de importación, vuelva atrás y ejecute LINK para generar los archivos ejecutables que no se generaron en el paso anterior. Tenga en cuenta que se debe especificar el archivo .exp correspondiente en la línea de vínculo.

   Si hubiera ejecutado la herramienta LIB para producir una biblioteca de importación para DLL1, LIB habría producido el archivo DLL1.exp también. Debe utilizar DLL1.exp como entrada de LINK al generar DLL1.dll.

La siguiente ilustración muestra una solución para dos archivos DLL, DLL1 y DLL2. Paso 1 es ejecutar LIB, con la opción /DEF establecida, en DLL1. Paso 1 produce DLL1.lib, una biblioteca de importación y DLL1.exp. En el paso 2, la biblioteca de importación se utiliza para generar DLL2, que a su vez genera una biblioteca de importación para los símbolos de DLL2. Paso 3 genera DLL1, con DLL1.exp y DLL2.lib como entrada. Tenga en cuenta que no es necesario un archivo .exp para DLL2 porque no se utilizó para generar la biblioteca de importación de DLL2 LIB.

![Uso de importaciones mutuas para vincular dos archivos DLL](media/vc37yj1.gif "con importaciones mutuas para vincular dos archivos DLL")<br/>
Vincular dos archivos DLL con importaciones mutuas

## <a name="limitations-of-afxext"></a>Limitaciones de _AFXEXT

Puede usar el `_AFXEXT` símbolo de preprocesador para la extensión siempre y cuando no tiene varias capas de DLL de extensión MFC de DLL MFC. Si tiene la extensión de MFC archivos DLL que llamar o derivar desde clases en su propia extensión MFC archivos DLL, que se derivan de las clases de MFC, debe utilizar su propio símbolo de preprocesador para evitar la ambigüedad.

El problema es que en Win32, debe declarar explícitamente todos los datos como **__declspec (dllexport)** si se van a exportarse desde un archivo DLL, y **__declspec (dllimport)** si se van a importar desde un archivo DLL. Al definir `_AFXEXT`, los encabezados de MFC, asegúrese de que **AFX_EXT_CLASS** está definida correctamente.

Cuando hay varios niveles, un símbolo como **AFX_EXT_CLASS** no es suficiente, porque un archivo DLL de extensión MFC podría exportar clases nuevas, así como importar otras clases desde otro archivo DLL de extensión MFC. Para solucionar este problema, utilice un símbolo de preprocesador especial que indica que se está compilando el archivo DLL, frente al uso de la DLL. Por ejemplo, imagine dos archivos DLL de extensión MFC, A.dll y B.dll. Cada uno de ellos exporta algunas clases en A.h y B.h, respectivamente. B.dll utiliza las clases de A.dll. Los archivos de encabezado sería algo parecido a esto:

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

A.dll se genera con `/D A_IMPL` y B.dll se genera con `/D B_IMPL`. Mediante el uso de símbolos independientes para cada archivo DLL, `CExampleB` se exporta y `CExampleA` se importa al compilar B.dll. `CExampleA` se exporta al generar A.dll y se importa al utiliza B.dll (o algún otro cliente).

Este tipo de disposición en capas no se puede realizar cuando se usa el método integrado **AFX_EXT_CLASS** y `_AFXEXT` símbolos de preprocesador. La técnica descrita anteriormente soluciona este problema en una manera que el mecanismo de MFC usa al generar sus tecnologías activas, base de datos y archivos DLL de extensión MFC de red.

## <a name="not-exporting-the-entire-class"></a>No exporte toda la clase

Cuando no se exporta una clase entera, tendrá que asegurarse de que los elementos de datos necesarios creados por las macros MFC se exportan correctamente. Esto puede hacerse mediante la redefinición de `AFX_DATA` macro específica de la clase. Esto debe hacerse siempre que no se exporte toda la clase.

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

- [Exportar desde un archivo DLL](exporting-from-a-dll.md)

- [Exportar desde un archivo DLL mediante. DEF (archivos)](exporting-from-a-dll-using-def-files.md)

- [Exportar desde un archivo DLL mediante__declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportar e importar utilizando AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Determinar qué método de exportación para usar](determining-which-exporting-method-to-use.md)

- [Importar a una aplicación mediante __declspec (dllimport)](importing-into-an-application-using-declspec-dllimport.md)

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [La utilidad LIB y la opción /DEF](reference/lib-reference.md)

## <a name="see-also"></a>Vea también

[Importar y exportar](importing-and-exporting.md)
