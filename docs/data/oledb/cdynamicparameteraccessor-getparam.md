---
title: 'CDynamicParameterAccessor:: GetParam | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicParameterAccessor::GetParam
- ATL.CDynamicParameterAccessor.GetParam
- CDynamicParameterAccessor::GetParam<ctype>
- CDynamicParameterAccessor.GetParam
- GetParam
- ATL::CDynamicParameterAccessor::GetParam<ctype>
- ATL::CDynamicParameterAccessor::GetParam
dev_langs:
- C++
helpviewer_keywords:
- GetParam method
ms.assetid: 893a6bf8-7b55-4f6d-8a10-a43b13be7f56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3596cf8fc445a5607c008be687c44cafb713049b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090906"
---
# <a name="cdynamicparameteraccessorgetparam"></a>CDynamicParameterAccessor::GetParam
Recupera los datos que no sean para un parámetro especificado desde el búfer de parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
template <class ctype>bool GetParam(DBORDINAL nParam,   
  ctype* pData) const throw();  

template <class ctype> bool GetParam(TCHAR* pParamName,   
   ctype* pData) const throw();  

void* GetParam(DBORDINAL nParam) const throw();  

void* GetParam(TCHAR* pParamName) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ctype`  
 Un parámetro de plantilla que es el tipo de datos.  
  
 `nParam`  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro basándose en su orden en el SQL o una llamada al procedimiento almacenado. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 `pParamName`  
 [in] El nombre del parámetro.  
  
 `pData`  
 [out] Puntero a la memoria que contiene los datos recuperados desde el búfer.  
  
## <a name="return-value"></a>Valor devuelto  
 En las versiones sin plantilla, apunta a la memoria que contiene los datos recuperados desde el búfer. En las versiones con plantilla, devuelve **true** en caso de éxito o **false** en caso de error.  
  
 Use `GetParam` para recuperar datos de parámetro que no sean del búfer. Use [GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md) para recuperar datos de parámetro de cadena desde el búfer.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)