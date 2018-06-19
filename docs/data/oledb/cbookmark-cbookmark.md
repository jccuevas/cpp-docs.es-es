---
title: 'CBookmark:: CBookmark | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class, constructor
ms.assetid: 84f4ad2b-67d4-4ba3-8b2b-656a66fb6298
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f7663c34fc9eea5f4262fea6b347c1b7899ace85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095240"
---
# <a name="cbookmarkcbookmark"></a>CBookmark::CBookmark
El constructor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      CBookmark();   

CBookmark(DBLENGTH nSize);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nSize`  
 [in] Tamaño del búfer del marcador en bytes.  
  
## <a name="remarks"></a>Comentarios  
 La primera función establece el búfer **NULL** y el tamaño de búfer en 0. La segunda función establece el tamaño de búfer en `nSize`y el búfer a una matriz de bytes de `nSize` bytes.  
  
> [!NOTE]
>  Esta función sólo está disponible en **CBookmark\<0 >**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CBookmark (Clase)](../../data/oledb/cbookmark-class.md)