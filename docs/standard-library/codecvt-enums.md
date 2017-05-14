---
title: '&lt;codecvt&gt; (Enumeraciones) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
caps.latest.revision: 10
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 268723c43d61761e2b0a01d337adecc3336e01f3
ms.contentlocale: es-es
ms.lasthandoff: 04/19/2017

---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt; (Enumeraciones)
  
##  <a name="codecvt_mode"></a>  codecvt_mode (Enumeración)  
 Especifica la información de configuración de las facetas de [configuración regional](../standard-library/locale-class.md).  
  
```  
enum codecvt_mode {  
    consume_header = 4,  
    generate_header = 2,  
    little_endian = 1  
 };  
```  
  
### <a name="remarks"></a>Comentarios  
 La enumeración define tres constantes que proporcionan información de configuración a las facetas de configuración regional declaradas en [\<codecvt>](../standard-library/codecvt.md). Los diferentes valores son:  
  
- `consume_header`, para consumir una secuencia de encabezados iniciales al leer una secuencia multibyte y determinar los modos endian de la secuencia multibyte que se va a leer  
  
- `generate_header`, para generar una secuencia de encabezados iniciales al escribir una secuencia multibyte para anunciar los modos endian de la secuencia multibyte siguiente que se va a escribir  
  
- `little_endian`, para generar una secuencia multibyte en orden little endian, en lugar del orden big endian predeterminado  
  
 Estas constantes pueden usar OR en combinaciones arbitrarias.  
  
## <a name="see-also"></a>Vea también  
 [\<codecvt>](../standard-library/codecvt.md)


