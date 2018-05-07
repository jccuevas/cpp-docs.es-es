---
title: 'CDynamicParameterAccessor:: Getparamname | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicParameterAccessor::GetParamName
- ATL.CDynamicParameterAccessor.GetParamName
- GetParamName
- CDynamicParameterAccessor.GetParamName
- ATL::CDynamicParameterAccessor::GetParamName
dev_langs:
- C++
helpviewer_keywords:
- GetParamName method
ms.assetid: 707c08ed-d3d0-4ce8-b23e-20b07202a3e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eee62bafbff5d8d9b174013e5165287a5b9f89cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicparameteraccessorgetparamname"></a>CDynamicParameterAccessor::GetParamName
Recupera el nombre del parámetro especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      LPOLESTR GetParamName(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nParam`  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro basándose en su orden en el SQL o una llamada al procedimiento almacenado. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
## <a name="return-value"></a>Valor devuelto  
 El nombre del parámetro especificado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)