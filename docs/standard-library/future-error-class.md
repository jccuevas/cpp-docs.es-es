---
title: future_error (Clase)
ms.date: 11/04/2016
f1_keywords:
- future/std::future_error
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
ms.openlocfilehash: ed3f9d63c45d0e185e3e1476094736d132822173
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447349"
---
# <a name="futureerror-class"></a>future_error (Clase)

Describe un objeto de excepción que pueden producir los métodos de tipos que administran objetos [future](../standard-library/future-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
class future_error : public logic_error {
public:
    future_error(error_code code);

const error_code& code() const throw();

const char *what() const throw();

};
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> futuro

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[logic_error (Clase)](../standard-library/logic-error-class.md)\
[error_code (Clase)](../standard-library/error-code-class.md)
