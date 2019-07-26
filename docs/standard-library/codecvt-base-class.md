---
title: codecvt_base (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_base
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
ms.openlocfilehash: 1a32ba5e583fdb20118a3397f1ddb326302f2de1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459386"
---
# <a name="codecvtbase-class"></a>codecvt_base (Clase)

Una clase base para la clase codecvt que se usa para definir un tipo de enumeración al `result`que se hace referencia como, que se usa como tipo de valor devuelto para las funciones miembro de la faceta para indicar el resultado de una conversión.

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

- `ok`Si la conversión entre las codificaciones de caracteres internas y externas se realiza correctamente.

- `partial`Si el destino no es lo suficientemente grande como para que la conversión se realice correctamente.

- `error`Si la secuencia de origen tiene un formato incorrecto.

- `noconv` si la función no realiza ninguna conversión.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
