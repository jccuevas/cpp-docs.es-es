---
title: operator&gt; (&lt;sample container&gt;) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- std::operator>
- operator>
- std::>
- '>'
dev_langs:
- C++
helpviewer_keywords:
- '> operator, comparing specific objects'
- operator >
ms.assetid: 49bd417a-3305-4ffa-9884-39d3904ed87d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 11bfc00a3e60851087e6417cfa0d8d1d187931c0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="operatorgt-ltsample-containergt"></a>operator&gt; (&lt;sample container&gt;)
> [!NOTE]
>  Este tema se incluye en la documentación de Visual C++ como un ejemplo no funcional de los contenedores usados en la biblioteca estándar de C++. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).  
  
 Sobrecarga **operator>** para comparar dos objetos de la clase de plantilla [Container](../standard-library/sample-container-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Ty>  
bool operator*gt;(
    const Container <Ty>& left,  
    const Container <Ty>& right);
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `right < left`.  
  
## <a name="see-also"></a>Vea también  
 [\<sample container>](../standard-library/sample-container.md)

