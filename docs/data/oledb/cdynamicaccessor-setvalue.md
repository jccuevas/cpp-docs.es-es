---
title: 'CDynamicAccessor:: SetValue | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
dev_langs:
- C++
helpviewer_keywords:
- SetValue method
ms.assetid: ecc18850-96e5-4845-abe5-ab34ad467238
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9322394f2b72b49afe988c371858d9ee580825ab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095682"
---
# <a name="cdynamicaccessorsetvalue"></a>CDynamicAccessor::SetValue
Almacena los datos en una columna especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <class ctype>
bool SetValue(   
   DBORDINAL nColumn,   
   constctype& data) throw( );  

template <class ctype>    
bool SetValue(   
   const CHAR * pColumnName,   
   const ctype& data) throw( );  

template <class ctype>   
bool SetValue(  
   const WCHAR *pColumnName,  
   const ctype& data) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ctype`  
 [in] Un parámetro de plantilla que controla cualquier tipo de datos excepto los tipos de cadena (**CHAR\***, **WCHAR\***), que requieren un tratamiento especial. `GetValue` usa el tipo de datos adecuado en función de lo que especifique aquí.  
  
 `pColumnName`  
 [in] Un puntero a una cadena de caracteres que contiene el nombre de columna.  
  
 `data`  
 [in] Puntero a la memoria que contiene los datos.  
  
 `nColumn`  
 [in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si lo hay.  
  
## <a name="return-value"></a>Valor devuelto  
 Si desea establecer los datos de cadena, utilice las versiones sin plantilla de `GetValue`. Las versiones sin plantilla de este método devuelven **void\***, que señala a la parte del búfer que contiene los datos de la columna especificada. Devuelve **NULL** si no se encuentra la columna.  
  
 Para los demás tipos de datos, resulta más sencillo de usar las versiones de plantillas de `GetValue`. Las versiones con plantilla devuelven **true** en caso de éxito o **false** en caso de error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)