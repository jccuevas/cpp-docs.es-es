---
title: Error del compilador C2813
ms.date: 11/04/2016
f1_keywords:
- C2813
helpviewer_keywords:
- C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
ms.openlocfilehash: 2cdf22d82046c66a50be0779f08e934a05555bb9
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810678"
---
# <a name="compiler-error-c2813"></a>Error del compilador C2813

no se admite la importación de \#con/MP

El error C2813 se genera si en un comando de compilador se especifica la opción del compilador **/MP** y dos o más archivos para compilar y uno o varios de los archivos contiene la directiva de preprocesador[#import](../../preprocessor/hash-import-directive-cpp.md) . La directiva [#import](../../preprocessor/hash-import-directive-cpp.md) genera clases de C++ a partir de los tipos de la biblioteca de tipos especificada y, a continuación, escribe las clases en dos archivos de encabezado. La directiva [#import](../../preprocessor/hash-import-directive-cpp.md) no se admite la directiva porque si varias unidades de compilación importan la misma biblioteca de tipos, las unidades entran en conflicto al intentar escribir los mismos archivos de encabezado al mismo tiempo.

Este error del compilador y la opción del compilador **/MP** son nuevas en Visual Studio 2008.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C2813. La línea de comandos del comentario "compile with:" indica al compilador que debe usar las opciones del compilador **/MP** y **/c** para compilar varios archivos. Al menos uno de los archivos contiene la directiva [#import](../../preprocessor/hash-import-directive-cpp.md) . El mismo archivo se usa dos veces para probar este ejemplo.

```cpp
// C2813.cpp
// compile with: /MP /c C2813.cpp C2813.cpp
#import "C:\windows\system32\stdole2.tlb"   // C2813
int main()
{
}
```
