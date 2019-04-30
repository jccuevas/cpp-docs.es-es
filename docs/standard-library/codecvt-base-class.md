---
title: codecvt_base (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_base
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
ms.openlocfilehash: 6f957c39f9c78fd182b7ba2a14bdab7f27db56ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405305"
---
# <a name="codecvtbase-class"></a>codecvt_base (Clase)

Una clase base para la clase codecvt que se utiliza para definir un tipo de enumeración denomina `result`, que se usa como el tipo de valor devuelto para las funciones miembro de faceta para indicar el resultado de una conversión.

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

- `ok` Si se realiza correctamente la conversión entre las codificaciones de caracteres internas y externas.

- `partial` Si el destino no es lo suficientemente grande como para la conversión se realice correctamente.

- `error` Si la secuencia de origen está enferma formada.

- `noconv` si la función no realiza ninguna conversión.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
