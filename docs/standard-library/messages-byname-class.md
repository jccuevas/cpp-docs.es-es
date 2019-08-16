---
title: messages_byname (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_byname
helpviewer_keywords:
- messages_byname class
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
ms.openlocfilehash: b8fe1ab2db792819831f5c50aa99a02559f71cdd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451805"
---
# <a name="messagesbyname-class"></a>messages_byname (Clase)

La clase de plantilla derivada describe un objeto que puede actuar como una faceta de mensajes de una configuración regional concreta, lo que permite la recuperación de mensajes localizados.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType>
class messages_byname : public messages<CharType> {
public:
    explicit messages_byname(
    const char *_Locname,
    size_t _Refs = 0);

    explicit messages_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~messages_byname();

};
```

### <a name="parameters"></a>Parámetros

*_Locname*\
Una configuración regional con nombre.

*_Refs*\
Un recuento de referencias inicial.

## <a name="remarks"></a>Comentarios

Su comportamiento viene determinado por el *_Locname*de configuración regional con nombre. Cada constructor inicializa su objeto base con [messages](../standard-library/messages-class.md#messages)\<CharType>( `_Refs`).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
