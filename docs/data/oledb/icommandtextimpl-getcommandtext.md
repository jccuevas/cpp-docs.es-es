---
title: ICommandTextImpl::GetCommandText | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
dev_langs:
- C++
helpviewer_keywords:
- GetCommandText method
ms.assetid: 0f8da470-b1c3-4573-974f-1acc111e3984
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a5da83e0be8b15c317e9bf97d2f11acc3d7f85e2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="icommandtextimplgetcommandtext"></a>ICommandTextImpl::GetCommandText
Devuelve el comando de texto establecido por la última llamada a [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(GetCommandText)(GUID * pguidDialect,   
   LPOLESTR * ppwszCommand);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) en el *referencia del programador OLE DB*. El *pguidDialect* parámetro se ignora de forma predeterminada.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [ICommandTextImpl (Clase)](../../data/oledb/icommandtextimpl-class.md)