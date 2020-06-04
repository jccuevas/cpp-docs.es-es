---
title: moneypunct_byname (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct_byname
helpviewer_keywords:
- moneypunct_byname class
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
ms.openlocfilehash: c687bc870e4d78cfe9174eb04ea09c34d6a9c955
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687656"
---
# <a name="moneypunct_byname-class"></a>moneypunct_byname (Clase)

Una plantilla de clase derivada que describe un objeto que puede actuar como una faceta `moneypunct` de una configuración regional determinada, habilitando el campo de entrada monetario de formato o los campos de salida monetarios.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType, bool Intl = false>
class moneypunct_byname : public moneypunct<CharType, Intl>
{
public:
    explicit moneypunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit moneypunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~moneypunct_byname();

};
```

## <a name="remarks"></a>Comentarios

Su comportamiento viene determinado por la configuración regional con nombre `_Locname`. Cada constructor inicializa su objeto base con [moneypunct](../standard-library/moneypunct-class.md#moneypunct)\<CharType, Intl>( `_Refs`).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
