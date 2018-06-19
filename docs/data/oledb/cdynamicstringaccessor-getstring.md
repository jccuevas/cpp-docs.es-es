---
title: 'CDynamicStringAccessor:: GetString | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
dev_langs:
- C++
helpviewer_keywords:
- GetString method
ms.assetid: 4af27f27-7589-49f5-93d8-6ef05c023c8a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cc23fe73eb0d804d0b53950885b1b83aba58ff91
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096553"
---
# <a name="cdynamicstringaccessorgetstring"></a>CDynamicStringAccessor::GetString
Recupera los datos de la columna especificada como una cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      BaseType* GetString(DBORDINAL nColumn) const throw();  

BaseType* GetString(const CHAR* pColumnName) const throw();  

BaseType* GetString(const WCHAR* pColumnName) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nColumn`  
 [in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si lo hay.  
  
 `pColumnName`  
 [in] Un puntero a una cadena de caracteres que contiene el nombre de columna.  
  
## <a name="return-value"></a>Valor devuelto  
 Recupera un puntero al valor de cadena de la columna especificada. El valor es de tipo ***BaseType***, que será **CHAR** o **WCHAR** dependiendo de si se ha definido _UNICODE o no. Devuelve NULL si no se encuentra la columna especificada.  
  
## <a name="remarks"></a>Comentarios  
 El segundo invalidar formulario toma el nombre de columna como una cadena ANSI. La tercera invalidar formulario toma el nombre de columna como una cadena Unicode.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicStringAccessor (Clase)](../../data/oledb/cdynamicstringaccessor-class.md)