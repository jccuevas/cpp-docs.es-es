---
title: Advertencia del compilador (nivel 1) C4691
ms.date: 11/04/2016
f1_keywords:
- C4691
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
ms.openlocfilehash: 8065129e20b627eb387421455527f6aaec3fdc2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175381"
---
# <a name="compiler-warning-level-1-c4691"></a>Advertencia del compilador (nivel 1) C4691

' type ': se esperaba el tipo al que se hace referencia en el ensamblado ' file ' sin referencia, tipo definido en la unidad de traducción actual que se usa en su lugar

No se hace referencia al archivo de metadatos que contiene la definición de tipo original y el compilador está utilizando una definición de tipo local.

En el caso de que se recompile el *archivo*, C4691 se puede omitir o desactivar con pragma [Warning](../../preprocessor/warning.md).  Es decir, si el archivo que se va a compilar es el mismo que el archivo donde el compilador espera encontrar la definición de tipo, puede omitir C4691.

Sin embargo, se puede producir un comportamiento inesperado si el compilador usa una definición que no es del mismo ensamblado al que se hace referencia en los metadatos; Los tipos CLR no solo se escriben con el nombre del tipo, sino también con el ensamblado.  Es decir, un tipo Z del ensamblado z. dll es diferente del tipo Z del ensamblado y. dll.

## <a name="example"></a>Ejemplo

Este ejemplo contiene la definición de tipo original.

```cpp
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

## <a name="example"></a>Ejemplo

En este ejemplo se hace referencia a C4691_a. dll y se declara un campo de tipo Original_Type.

```cpp
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4691.  Observe que este ejemplo contiene una definición para Original_Type y no hace referencia a C4691a. dll.

Para resolverlo, haga referencia al archivo de metadatos que contiene la definición de tipo original y quite la declaración y la definición locales.

```cpp
// C4691_c.cpp
// compile with: /clr /LD /W1
// C4691 expected

// Uncomment the following line to resolve.
// #using "C4691_a.dll"
#using "C4691_b.dll"

// Delete the following line to resolve.
ref class Original_Type;

public ref class MyClass : Client {};
```
