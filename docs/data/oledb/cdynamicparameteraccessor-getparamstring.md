---
title: 'CDynamicParameterAccessor:: Getparamstring | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicParameterAccessor.GetParamString
- GetParamString
- CDynamicParameterAccessor::GetParamString
- ATL.CDynamicParameterAccessor.GetParamString
- ATL::CDynamicParameterAccessor::GetParamString
dev_langs:
- C++
helpviewer_keywords:
- GetParamString method
ms.assetid: 078c2b1c-7072-47c1-a203-f47e75363f91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b8dadcb70dd29f1a70aea288eb0f63b22591561e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicparameteraccessorgetparamstring"></a>CDynamicParameterAccessor::GetParamString
Recupera los datos de cadena del parámetro especificado almacenado en el búfer.  
  
## <a name="syntax"></a>Sintaxis  
  
```
bool GetParamString(DBORDINAL nParam,  
  CSimpleStringA& strOutput) throw();bool GetParamString(DBORDINAL nParam,  
  CSimpleStringW& strOutput) throw();bool GetParamString(DBORDINAL nParam,  
  CHAR* pBuffer,  
   size_t* pMaxLen) throw();bool GetParamString(DBORDINAL nParam,  
  WCHAR* pBuffer,  
   size_t* pMaxLen) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nParam`  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro basándose en su orden en el SQL o una llamada al procedimiento almacenado. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 `strOutput`  
 [out] El ANSI (**CSimpleStringA**) o Unicode (**CSimpleStringW**) los datos del parámetro especificado de cadena. Debe pasar un parámetro de tipo `CString`, por ejemplo:  
  
 [!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]  
  
 `pBuffer`  
 [out] Un puntero a ANSI (**CHAR**) o Unicode (**WCHAR**) los datos del parámetro especificado de cadena.  
  
 `pMaxLen`  
 [out] Un puntero al tamaño del búfer señalado por `pBuffer` (en caracteres, incluido el carácter NULL final).  
  
## <a name="remarks"></a>Comentarios  
 Devuelve **true** en caso de éxito o **false** en caso de error.  
  
 Si `pBuffer` es NULL, este método establecerá el tamaño de búfer necesario en la memoria que señala `pMaxLen` y devolver **true** sin copiar los datos.  
  
 Este método se producirá un error si el búfer `pBuffer` no es lo suficientemente grande como para contener toda la cadena.  
  
 Use `GetParamString` para recuperar datos de parámetro de cadena desde el búfer. Use [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) para recuperar datos de parámetro que no sean del búfer.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)