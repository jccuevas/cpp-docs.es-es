---
title: hash&lt;string_view&gt; especialización
ms.date: 04/19/2019
f1_keywords:
- xstring/basic_string_view::hash
helpviewer_keywords:
- std::basic_string_view::hash
ms.openlocfilehash: 60b6fdecc371ee950532dee3f69cc8dd07b8b5eb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346963"
---
# <a name="hashltstringviewgt-specialization"></a>hash&lt;string_view&gt; especialización

Una especialización de plantilla que genera un valor hash, dado una string_view.

```cpp
template <class CharType, class Traits>
struct hash<basic_string_view<CharType, Traits>>
{
    typedef basic_string_view<CharType, Traits> argument_type;
    typedef size_t result_type;

    size_t operator()(const basic_string_view<CharType, Traits>) const
        noexcept;
};
```
### <a name="remarks"></a>Comentarios

El hash de un string_view igual que el hash del objeto de cadena subyacente.

### <a name="example"></a>Ejemplo

```cpp
//compile with: /std:c++17
#include <string>
#include <string_view>
#include <iostream>

using namespace std;

int main()
{
    string_view sv{ "Hello world" };
    string s{ "Hello world" };
    cout << boolalpha << (hash<string_view>{}(sv)
        == hash<string>{}(s)); // true
}
```