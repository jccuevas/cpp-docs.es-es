---
title: register (Especificador de clase de almacenamiento) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 9804516a890ff7a58f0eefb70fb85fa3264c93c4
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="register-storage-class-specifier"></a>register (Especificador de clase de almacenamiento)
**Específicos de Microsoft**  
  
 El compilador de Microsoft C/C++ no admite solicitudes de usuario para variables de registro. Sin embargo, a efectos de portabilidad, el compilador acepta toda la demás semántica asociada a la palabra clave **register**. Por ejemplo, no puede aplicar el operador unario de dirección (**&**) a un objeto del registro ni puede usar la palabra clave **register** en matrices.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Especificadores de clase de almacenamiento para las declaraciones de nivel interno](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
