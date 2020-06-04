---
title: codecvt_byname (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_byname
helpviewer_keywords:
- codecvt_byname class
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
ms.openlocfilehash: b48f01126eba7082230fc5e19150d42d1dfad2f3
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688295"
---
# <a name="codecvt_byname-class"></a>codecvt_byname (Clase)

Una plantilla de clase derivada que describe un objeto que puede actuar como una faceta de intercalación de una configuración regional determinada, lo que permite la recuperación de información específica de un área cultural relativa a las conversiones.

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

@No__t_1 *_Locname*
Una configuración regional con nombre.

@No__t_1 *_Refs*
Un recuento de referencias inicial.

## <a name="remarks"></a>Comentarios

Las facetas byname se crean de forma automática cuando se crea una configuración regional con nombre.

Su comportamiento viene determinado por el *_Locname*de configuración regional con nombre. Cada constructor inicializa su objeto base con [codecvt](../standard-library/codecvt-class.md)\<CharType, Byte. StateType>( `_Refs`).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
