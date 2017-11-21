---
title: operator!= | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::!=
- '!='
- std::operator!=
- std.operator!=
- std.!=
- operator!=
dev_langs: C++
helpviewer_keywords:
- '!= operator'
- operator!=
- operator !=
ms.assetid: ef2be7f0-1c94-4edc-b65c-731fddd519f4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9c6737138208a9703ca7de7ce3048a06606abcd5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="operator"></a>operator!=
> [!NOTE]
>  Este tema se incluye en la documentación de Visual C++ como un ejemplo no funcional de los contenedores usados en la biblioteca estándar de C++. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).  
  
 Sobrecarga `operator!=` para comparar dos objetos de la clase de plantilla [Container](../standard-library/sample-container-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Ty>  
bool operator!=(
    const Container <Ty>& left,  
    const Container <Ty>& right);
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `!(left == right)`.  
  
## <a name="see-also"></a>Vea también  
 [\<sample container>](../standard-library/sample-container.md)

