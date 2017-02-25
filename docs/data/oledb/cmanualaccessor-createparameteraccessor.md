---
title: "CManualAccessor::CreateParameterAccessor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CManualAccessor::CreateParameterAccessor"
  - "ATL.CManualAccessor.CreateParameterAccessor"
  - "CManualAccessor.CreateParameterAccessor"
  - "CreateParameterAccessor"
  - "CManualAccessor::CreateParameterAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateParameterAccessor (método)"
ms.assetid: d0a2095b-b37c-4472-accc-45ef365a18c8
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CManualAccessor::CreateParameterAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigna memoria para las estructuras de enlace de parámetro e inicializa los miembros de datos de parámetro.  
  
## Sintaxis  
  
```  
  
      HRESULT CreateParameterAccessor(   
   int nBindEntries,   
   void* pBuffer,   
   DBLENGTH nBufferSize    
) throw( );  
```  
  
#### Parámetros  
 `nBindEntries`  
 \[in\] Número de columnas.  
  
 `pBuffer`  
 \[in\] Un puntero al búfer donde se almacenan las columnas de entrada.  
  
 `nBufferSize`  
 \[in\] El tamaño del búfer en bytes.  
  
## Valor devuelto  
 Uno de los valores estándar de `HRESULT` .  
  
## Comentarios  
 Debe llamar a esta función antes de llamar a [AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CManualAccessor \(Clase\)](../../data/oledb/cmanualaccessor-class.md)   
 [CManualAccessor::CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)   
 [CManualAccessor::AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)