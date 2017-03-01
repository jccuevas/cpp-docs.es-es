---
title: '&lt;codecvt&gt; (Enumeraciones) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 21162b7c25e09f2f77d2da1f4ee7797e68ec1e94
ms.lasthandoff: 02/24/2017

---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt; (Enumeraciones)
  
##  <a name="a-namecodecvtmodeenumerationa--codecvtmode-enumeration"></a><a name="codecvt_mode_enumeration"></a>  codecvt_mode (Enumeración)  
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


