---
title: numpunct_byname (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::numpunct_byname
helpviewer_keywords:
- numpunct_byname class
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
ms.openlocfilehash: 0c9eb565c2dbf54da449411aa11a4c5661debf1d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452317"
---
# <a name="numpunctbyname-class"></a>numpunct_byname (Clase)

La clase de plantilla derivada describe un objeto que puede actuar como una faceta `numpunct` de una configuración regional concreta, lo que habilita el formato y la puntuación de expresiones numéricas y booleanas.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType>
class numpunct_byname : public numpunct<Elem> {
public:
    explicit numpunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit numpunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~numpunct_byname();

};
```

## <a name="remarks"></a>Comentarios

Su comportamiento viene determinado por la configuración regional [con nombre](../standard-library/locale-class.md#name) `_Locname`. El constructor inicializa su objeto base con [numpunct](../standard-library/numpunct-class.md#numpunct)\<CharType>( `_Refs`).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
