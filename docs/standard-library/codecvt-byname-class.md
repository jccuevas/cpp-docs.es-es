---
title: codecvt_byname (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- xlocale/std::codecvt_byname
dev_langs:
- C++
helpviewer_keywords:
- codecvt_byname class
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b1c7ee779e8ad4a7f39df4e92a1b9ed2030742a
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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

`_Locname` Una configuración regional con nombre.

`_Refs` Un recuento de referencia inicial.

## <a name="remarks"></a>Comentarios

Las facetas byname se crean de forma automática cuando se crea una configuración regional con nombre.

Su comportamiento viene determinado por la configuración regional con nombre `_Locname`. Cada constructor inicializa su objeto base con [codecvt](../standard-library/codecvt-class.md)\<CharType, Byte. StateType>( `_Refs`).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
