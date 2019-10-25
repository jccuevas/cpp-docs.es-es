---
title: collate_byname (Clase)
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: 3e9a256ac7bdb5f6d077746fe2a08990ed41e931
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688269"
---
# <a name="collate_byname-class"></a>collate_byname (Clase)

Una plantilla de clase derivada que describe un objeto que puede actuar como una faceta de intercalación de una configuración regional determinada, lo que permite la recuperación de información específica de un área cultural relativa a las convenciones de ordenación de cadenas.

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

@No__t_1 *_Locname*
Una configuración regional con nombre.

@No__t_1 *_Refs*
Un recuento de referencias inicial.

## <a name="remarks"></a>Comentarios

La plantilla de clase describe un objeto que puede actuar como una [faceta de configuración regional](../standard-library/locale-class.md#facet_class) de tipo [collate](../standard-library/collate-class.md#collate) \<CharType >. Su comportamiento viene determinado por el *_Locname*de configuración regional [con nombre](../standard-library/locale-class.md#name) . Cada constructor inicializa su objeto base con [collate](../standard-library/collate-class.md#collate)\<CharType>( `_Refs`).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
