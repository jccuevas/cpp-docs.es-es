---
title: 'CDBPropSet:: AddProperty | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
dev_langs:
- C++
helpviewer_keywords:
- AddProperty method
ms.assetid: dc9539d3-1ee4-40f3-9281-2068e6d65e93
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7daa1146bbd4e288d20c59f7f1fff8c4bcbbb455
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cdbpropsetaddproperty"></a>CDBPropSet::AddProperty
Agrega una propiedad al conjunto de propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```
bool AddProperty(DWORD dwPropertyID,   
   constVARIANT& var,   
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   LPCSTR szValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   LPCWSTR szValue,DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   bool bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   BYTE bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   short nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   long nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   float fltValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   double dblValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   CY cyValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *dwPropertyID*  
 [in] Id. de la propiedad que se va a agregar. Utilizado para inicializar el **dwPropertyID** de la `DBPROP` estructura agregado al conjunto de propiedades.  
  
 `var`  
 [in] Una variante que se usa para inicializar el valor de propiedad para el `DBPROP` estructura agregado al conjunto de propiedades.  
  
 `szValue`  
 [in] Una cadena utilizada para inicializar el valor de propiedad para el `DBPROP` estructura agregado al conjunto de propiedades.  
  
 `bValue`  
 [in] A **bytes** o valor booleano utilizado para inicializar el valor de propiedad para el `DBPROP` estructura agregado al conjunto de propiedades.  
  
 `nValue`  
 [in] Un valor entero utilizado para inicializar el valor de propiedad para el `DBPROP` estructura agregado al conjunto de propiedades.  
  
 *fltValue*  
 [in] Un valor de punto flotante que se utiliza para inicializar el valor de propiedad para el `DBPROP` estructura agregado al conjunto de propiedades.  
  
 `dblValue`  
 [in] Un valor de punto flotante de precisión doble utilizado para inicializar el valor de propiedad para el `DBPROP` estructura agregado al conjunto de propiedades.  
  
 `cyValue`  
 [in] Un valor de moneda CY utilizado para inicializar el valor de propiedad para el `DBPROP` estructura agregado al conjunto de propiedades.  
  
## <a name="return-value"></a>Valor devuelto  
 **True** si la propiedad se agregó correctamente. en caso contrario, **false**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDBPropSet (clase)](../../data/oledb/cdbpropset-class.md)   
 [Estructura DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx)