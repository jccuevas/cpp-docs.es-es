---
title: typename
ms.date: 11/04/2016
f1_keywords:
- typename_cpp
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
ms.openlocfilehash: 789bb879922bbd96a04085159205d02fb7f495c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160689"
---
# <a name="typename"></a>typename

En las definiciones de plantilla, proporciona una sugerencia al compilador de que un identificador desconocido es un tipo. En las listas de parámetros de plantilla, se usa para especificar un parámetro de tipo.

## <a name="syntax"></a>Sintaxis

```
typename identifier;
```

## <a name="remarks"></a>Observaciones

Esta palabra clave debe usarse si un nombre de una definición de plantilla es un nombre completo que depende de un argumento de plantilla; es opcional si el nombre completo no es dependiente. Para obtener más información, vea [plantillas y resolución de nombres](../cpp/templates-and-name-resolution.md).

**TypeName** puede ser utilizado por cualquier tipo en cualquier parte de una declaración o definición de plantilla. No se permite en la lista de clases base, salvo como argumento de plantilla de una clase base de plantilla.

```cpp
template <class T>
class C1 : typename T::InnerType // Error - typename not allowed.
{};
template <class T>
class C2 : A<typename T::InnerType>  // typename OK.
{};
```

La palabra clave **TypeName** también puede usarse en lugar de la **clase** en las listas de parámetros de plantilla. Por ejemplo, las siguientes instrucciones son semánticamente equivalentes:

```cpp
template<class T1, class T2>...
template<typename T1, typename T2>...
```

## <a name="example"></a>Ejemplo

```cpp
// typename.cpp
template<class T> class X
{
   typename T::Y m_y;   // treat Y as a type
};

int main()
{
}
```

## <a name="see-also"></a>Consulte también

[Templates](../cpp/templates-cpp.md) (Plantillas [C++])<br/>
[Palabras clave](../cpp/keywords-cpp.md)
