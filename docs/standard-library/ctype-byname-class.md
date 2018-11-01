---
title: ctype_byname (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype_byname
helpviewer_keywords:
- ctype_byname class
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
ms.openlocfilehash: d998747045ece765269ddb013b525b8c06fcdf8b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517746"
---
# <a name="ctypebyname-class"></a>ctype_byname (Clase)

La clase de plantilla derivada describe un objeto que puede actuar como una faceta ctype de una configuración regional concreta, habilitando la clasificación y conversión de caracteres entre mayúsculas y minúsculas y entre los conjuntos de caracteres especificados en la configuración regional y nativa.

## <a name="syntax"></a>Sintaxis

```cpp
template <class _Elem>
class ctype_byname : public ctype<_Elem>
{
public:
    explicit ctype_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit ctype_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual __CLR_OR_THIS_CALL ~ctype_byname();

};
```

## <a name="remarks"></a>Comentarios

Su comportamiento viene determinado por la configuración regional con nombre `_Locname`. Cada constructor inicializa su objeto base con [ctype](../standard-library/ctype-class.md)\<CharType>( `_Refs`) o el equivalente de la clase base `ctype<char>`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
