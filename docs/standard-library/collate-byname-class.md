---
title: collate_byname (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- locale/std::collate_byname
dev_langs:
- C++
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b60e5aebcab11e839b6b1e6168aaac55a0202b7c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110245"
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

*_Locname*<br/>
Una configuración regional con nombre.

*_Refs*<br/>
Un recuento de referencias inicial.

## <a name="remarks"></a>Comentarios

La clase de plantilla describe un objeto que puede actuar como una [faceta de configuración regional](../standard-library/locale-class.md#facet_class) de tipo [collate](../standard-library/collate-class.md#collate)\<CharType>. Su comportamiento viene determinado por la [denominado](../standard-library/locale-class.md#name) configuración regional *_Locname*. Cada constructor inicializa su objeto base con [collate](../standard-library/collate-class.md#collate)\<CharType>( `_Refs`).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
