---
title: "CDBErrorInfo::GetErrorRecords | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDBErrorInfo.GetErrorRecords"
  - "ATL.CDBErrorInfo.GetErrorRecords"
  - "ATL::CDBErrorInfo::GetErrorRecords"
  - "GetErrorRecords"
  - "CDBErrorInfo::GetErrorRecords"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorRecords (método)"
ms.assetid: 07746774-bcca-4833-8f55-a619e9777c17
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBErrorInfo::GetErrorRecords
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene los registros de errores para el objeto especificado.  
  
## Sintaxis  
  
```  
  
      HRESULT GetErrorRecords(   
   IUnknown* pUnk,   
   const IID& iid,   
   ULONG* pcRecords    
) throw( );  
HRESULT GetErrorRecords(   
   ULONG* pcRecords    
) throw( );  
```  
  
#### Parámetros  
 *punky*  
 \[in\] Interfaz al objeto para que recopile los registros de error.  
  
 `iid`  
 \[in\] El IID de la interfaz asociada al error.  
  
 *pcRecords*  
 \[out\] Un puntero al recuento \(basado en uno\) de registros de error.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Utilice el primer formulario de la función si desea comprobar que interfaz para obtener la información de error.  Si no, use el segundo formulario.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDBErrorInfo \(Clase\)](../../data/oledb/cdberrorinfo-class.md)