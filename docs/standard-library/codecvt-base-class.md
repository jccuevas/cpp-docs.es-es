---
title: codecvt_base (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocale/std::codecvt_base
dev_langs:
- C++
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abe2a27a79705e9850df2c9fb54037278abd8cd5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="codecvtbase-class"></a>codecvt_base (Clase)

Una clase base de la clase codecvt que se usa para definir un tipo de enumeración al que se hace referencia como **result**, que se usa como el tipo de valor devuelto para las funciones miembro de la faceta para indicar el resultado de una conversión.

## <a name="syntax"></a>Sintaxis

```cpp
class codecvt_base : public locale::facet {
public:
    enum result {ok, partial, error, noconv};
    codecvt_base( size_t _Refs = 0);
    bool always_noconv() const;
    int max_length() const;
    int encoding() const;
    ~codecvt_base()

protected:
    virtual bool do_always_noconv() const;
    virtual int do_max_length() const;
    virtual int do_encoding() const;
};
```

## <a name="remarks"></a>Comentarios

La clase describe una enumeración común a todas las especializaciones de la clase de plantilla [codecvt](../standard-library/codecvt-class.md). El resultado de la enumeración describe los posibles valores devueltos de [do_in](../standard-library/codecvt-class.md#do_in) o [do_out](../standard-library/codecvt-class.md#do_out):

- **ok** si la conversión entre las codificaciones de caracteres internas y externas se realiza correctamente.

- **partial** si el origen no es suficiente o si el destino no es lo suficientemente grande como para que la conversión se realice correctamente.

- **error** si la secuencia de origen tiene un formato incorrecto.

- **noconv** si la función no realiza ninguna conversión.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
