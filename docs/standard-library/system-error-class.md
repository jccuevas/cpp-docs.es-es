---
title: system_error (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- system_error/std::system_error
dev_langs:
- C++
helpviewer_keywords:
- system_error class
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bde8e448d54be41516e65969f60b0651cacc8ef1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854563"
---
# <a name="systemerror-class"></a>system_error (Clase)

Representa la clase base para todas las excepciones que se inician para notificar un error de sistema de bajo nivel.

## <a name="syntax"></a>Sintaxis

```cpp
class system_error : public runtime_error {
public:
    explicit system_error(error_code _Errcode,
    const string& _Message = "");

    system_error(error_code _Errcode,
    const char *_Message);

    system_error(error_code::value_type _Errval,
    const error_category& _Errcat,
    const string& _Message);

    system_error(error_code::value_type _Errval,
    const error_category& _Errcat,
    const char *_Message);
const error_code& code() const throw();
const error_code& code() const throw();

};
```

## <a name="remarks"></a>Comentarios

El valor devuelto por `what` en la clase [exception](../standard-library/exception-class.md) se construye a partir de `_Message` y el objeto almacenado de tipo [error_code](../standard-library/error-code-class.md) (ya sea `code` o `error_code(_Errval, _Errcat)`).

La función miembro `code` devuelve el objeto [error_code](../standard-library/error-code-class.md) almacenado.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<system_error>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<system_error>](../standard-library/system-error.md)<br/>
