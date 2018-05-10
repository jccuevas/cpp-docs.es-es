---
title: register (Especificador de clase de almacenamiento) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 211f623923286e598f495920bcbdac3a9321b13a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="register-storage-class-specifier"></a>register (Especificador de clase de almacenamiento)
**Específicos de Microsoft**  
  
 El compilador de Microsoft C/C++ no admite solicitudes de usuario para variables de registro. Sin embargo, a efectos de portabilidad, el compilador acepta toda la demás semántica asociada a la palabra clave **register**. Por ejemplo, no puede aplicar el operador unario de dirección (**&**) a un objeto del registro ni puede usar la palabra clave **register** en matrices.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Especificadores de clase de almacenamiento para las declaraciones de nivel interno](../c-language/storage-class-specifiers-for-internal-level-declarations.md)