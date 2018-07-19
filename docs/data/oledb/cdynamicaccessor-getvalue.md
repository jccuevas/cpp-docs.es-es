---
title: 'CDynamicAccessor:: GetValue | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
dev_langs:
- C++
helpviewer_keywords:
- GetValue method
ms.assetid: 553f44af-68bc-4cb6-8774-e0940003fa90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7e43707d4697fbbeece5475f71b7e2f93e731772
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096423"
---
# <a name="cdynamicaccessorgetvalue"></a>CDynamicAccessor::GetValue
Recupera los datos de una columna especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
void* GetValue(DBORDINAL nColumn) const throw();  

void* GetValue(const CHAR* pColumnName) const throw();  

void* GetValue(const WCHAR* pColumnName) const throw();  

template < class ctype >
bool GetValue(DBORDINAL nColumn, ctype* pData) const throw();  

template < class ctype >  
bool GetValue(const CHAR* pColumnName, ctype* pData) const throw();  

template < class ctype >  
bool GetValue(const WCHAR* pColumnName, ctype* pData) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ctype`  
 [in] Un parámetro de plantilla que controla cualquier tipo de datos excepto los tipos de cadena (**CHAR\***, **WCHAR\***), que requieren un tratamiento especial. `GetValue` usa el tipo de datos adecuado en función de lo que especifique aquí.  
  
 `nColumn`  
 [in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si lo hay.  
  
 `pColumnName`  
 [in] El nombre de columna.  
  
 `pData`  
 [out] Puntero al contenido de la columna especificada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si desea pasar datos de cadena, utilice las versiones sin plantilla de `GetValue`. Las versiones sin plantilla de este método devuelven **void\***, que señala a la parte del búfer que contiene los datos de la columna especificada. Devuelve **NULL** si no se encuentra la columna.  
  
 Para los demás tipos de datos, resulta más sencillo de usar las versiones de plantillas de `GetValue`. Las versiones con plantilla devuelven **true** en caso de éxito o **false** en caso de error.  
  
## <a name="remarks"></a>Comentarios  
 Utilice las versiones sin plantilla para devolver las columnas que contienen cadenas y las versiones con plantilla para las columnas que contienen otros tipos de datos.  
  
 En modo de depuración, obtendrá una aserción si el tamaño de `pData` no es igual al tamaño de la columna a la que señala.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)