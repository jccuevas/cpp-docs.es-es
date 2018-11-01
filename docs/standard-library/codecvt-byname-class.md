---
title: codecvt_byname (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_byname
helpviewer_keywords:
- codecvt_byname class
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
ms.openlocfilehash: 62aac6abca3dce45ff3cc875823df04c69618b10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641589"
---
# <a name="codecvtbyname-class"></a>codecvt_byname (Clase)

Una clase de plantilla derivada que describe un objeto que puede actuar como faceta de intercalación de una configuración regional concreta, lo que permite la recuperación de información específica de un área cultural relativa a las conversiones.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType, class Byte, class StateType>
class codecvt_byname: public codecvt<CharType, Byte, StateType> {
public:
    explicit codecvt_byname(
    const char* _Locname,
    size_t _Refs = 0);
```

```cpp
explicit codecvt_byname(
    const string& _Locname,
    size_t _Refs = 0);
```

```cpp
protected:
    virtual ~codecvt_byname();

};
```

### <a name="parameters"></a>Parámetros

*_Locname*<br/>
Una configuración regional con nombre.

*_Refs*<br/>
Un recuento de referencias inicial.

## <a name="remarks"></a>Comentarios

Las facetas byname se crean de forma automática cuando se crea una configuración regional con nombre.

Su comportamiento viene determinado por la configuración regional con nombre *_Locname*. Cada constructor inicializa su objeto base con [codecvt](../standard-library/codecvt-class.md)\<CharType, Byte. StateType>( `_Refs`).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
