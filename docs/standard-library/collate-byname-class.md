---
title: collate_byname (Clase)
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: b8ed428da05e706796a981b8ca9d601033156c6f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458625"
---
# <a name="collatebyname-class"></a>collate_byname (Clase)

Una clase de plantilla derivada que describe un objeto que puede actuar como una faceta de intercalación de una configuración regional concreta, lo que permite la recuperación de información específica de un área cultural relativa a las convenciones de ordenación de cadenas.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```

### <a name="parameters"></a>Parámetros

*_Locname*\
Una configuración regional con nombre.

*_Refs*\
Un recuento de referencias inicial.

## <a name="remarks"></a>Comentarios

La clase de plantilla describe un objeto que puede actuar como una [faceta de configuración regional](../standard-library/locale-class.md#facet_class) de tipo [collate](../standard-library/collate-class.md#collate)\<CharType>. Su comportamiento viene determinado por el *_Locname*de configuración regional [con nombre](../standard-library/locale-class.md#name) . Cada constructor inicializa su objeto base con [collate](../standard-library/collate-class.md#collate)\<CharType>( `_Refs`).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
