---
title: "CDynamicParameterAccessor::SetParam | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDynamicParameterAccessor::SetParam"
  - "ATL::CDynamicParameterAccessor::SetParam<ctype>"
  - "CDynamicParameterAccessor.SetParam"
  - "ATL.CDynamicParameterAccessor.SetParam"
  - "SetParam"
  - "CDynamicParameterAccessor:SetParam"
  - "CDynamicParameterAccessor::SetParam<ctype>"
  - "CDynamicParameterAccessor::SetParam"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetParam (método)"
ms.assetid: e2349220-545c-46ad-90da-9113ac52551a
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CDynamicParameterAccessor::SetParam
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el búfer de parámetro con los datos especificados \(de la que no son de cadena\).  
  
## Sintaxis  
  
```  
  
      template < class   
      ctype >  
bool SetParam(  
   DBORDINAL nParam,  
   const ctype* pData,  
   DBSTATUS status = DBSTATUS_S_OK  
) throw( );  
template < class ctype >  
bool SetParam(  
   TCHAR* pParamName,  
   const ctype* pData,  
   DBSTATUS status = DBSTATUS_S_OK  
) throw( );  
```  
  
#### Parámetros  
 `ctype`  
 Un parámetro con plantillas que es el tipo de datos.  
  
 `nParam`  
 \[in\] El parámetro número \(desplazamiento desde 1\).  El parámetro 0 se reserva por valores devueltos.  El parámetro número es el índice del parámetro basándose en su orden de SQL o la llamada a un procedimiento almacenado.  Por ejemplo:  
  
 [!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/CPP/cdynamicparameteraccessor-setparam_1.cpp)]  
  
 `pParamName`  
 \[in\] Nombre del parámetro.  
  
 `pData`  
 \[in\] El puntero a la memoria que contiene los datos que se van a escribir en el búfer.  
  
 *status*  
 \[in\] El estado de la columna de `DBSTATUS` .  Para obtener información sobre los valores de `DBSTATUS` , vea [Estado](https://msdn.microsoft.com/en-us/library/ms722617.aspx) en *la referencia del*programador, o la búsqueda de `DBSTATUS` en oledb.h.  
  
## Valor devuelto  
 Devuelve **true** en correctamente o **false** en el error.  
  
 Utilice `SetParam` para establecer datos recursos de parámetro en el búfer.  Utilice [SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md) para establecer datos de parámetro de cadena en el búfer.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicParameterAccessor \(Clase\)](../../data/oledb/cdynamicparameteraccessor-class.md)