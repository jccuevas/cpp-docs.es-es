---
title: time_get_byname (Clase)
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get_byname
helpviewer_keywords:
- time_get_byname class
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
ms.openlocfilehash: e18f210dba03d66fa3a4ea111a6dfc61f0d0c12a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412012"
---
# <a name="timegetbyname-class"></a>time_get_byname (Clase)

La clase de plantilla derivada describe un objeto que puede actuar como una faceta de configuración regional de tipo `time_get`\<CharType, InputIterator>.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class InputIterator =
    istreambuf_iterator<CharType, char_traits<CharType>>>
class time_get_byname : public time_get<CharType, InputIterator>
{
public:
    explicit time_get_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_get_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_get_byname()
};
```

### <a name="parameters"></a>Parámetros

*_Locname*<br/>
Una configuración regional con nombre.

*_Refs*<br/>
Un recuento de referencias inicial.

## <a name="requirements"></a>Requisitos

Su comportamiento viene determinado por la configuración regional con nombre *_Locname*. Cada constructor inicializa su objeto base con [time_get](../standard-library/time-get-class.md#time_get)\<CharType, InputIterator>( `_Refs`).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
