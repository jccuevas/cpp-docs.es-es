---
title: register (Especificador de clase de almacenamiento)
ms.date: 11/04/2016
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
ms.openlocfilehash: 0fac6db2254a909d0ec558a7e76f7ccf32aa7ac3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325252"
---
# <a name="register-storage-class-specifier"></a>register (Especificador de clase de almacenamiento)

**Específicos de Microsoft**

El compilador de Microsoft C/C++ no admite solicitudes de usuario para variables de registro. Sin embargo, a efectos de portabilidad, el compilador acepta toda la demás semántica asociada a la palabra clave **register**. Por ejemplo, no puede aplicar el operador unario de dirección ( **&** ) a un objeto del registro ni puede usar la palabra clave **register** en matrices.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Especificadores de clase de almacenamiento para las declaraciones de nivel interno](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
