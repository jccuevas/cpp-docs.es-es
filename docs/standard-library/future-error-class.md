---
title: future_error (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::future_error
dev_langs:
- C++
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 07d01d2efc3aadf1d8b5a585b7f4c7b8b76d87cc
ms.contentlocale: es-es
ms.lasthandoff: 04/19/2017

---
# <a name="futureerror-class"></a>future_error (Clase)
Describe un objeto de excepción que pueden producir los métodos de tipos que administran objetos [future](../standard-library/future-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```
class future_error : public logic_error {
public:
    future_error(error_code code);

const error_code& code() const throw();

const char *what() const throw();

};
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<futura >  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [logic_error (Clase)](../standard-library/logic-error-class.md)   
 [error_code (Clase)](../standard-library/error-code-class.md)

