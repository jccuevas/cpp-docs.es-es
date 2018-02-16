---
title: CDynamicParameterAccessor::GetParamType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicParameterAccessor.GetParamType
- CDynamicParameterAccessor:GetParamType
- CDynamicParameterAccessor::GetParamType
- ATL.CDynamicParameterAccessor.GetParamType
- GetParamType
- ATL::CDynamicParameterAccessor::GetParamType
dev_langs:
- C++
helpviewer_keywords:
- GetParamType method
ms.assetid: d9c46775-c2a6-4100-8b69-99f13c52958b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2df37a426876217ce024e77cb9be4e4abcf52bd5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicparameteraccessorgetparamtype"></a>CDynamicParameterAccessor::GetParamType
Recupera el tipo de datos de un parámetro especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```
bool GetParamType(DBORDINAL nParam,  
  DBTYPE* pType) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nParam`  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro basándose en su orden en el SQL o una llamada al procedimiento almacenado. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 `pType`  
 [out] Un puntero a la variable que contiene el tipo de datos del parámetro especificado.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve **true** en caso de éxito o **false** en caso de error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)