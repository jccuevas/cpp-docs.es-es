---
title: "CManualAccessor::CreateAccessor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CManualAccessor::CreateAccessor"
  - "CreateAccessor"
  - "ATL.CManualAccessor.CreateAccessor"
  - "CManualAccessor.CreateAccessor"
  - "CManualAccessor::CreateAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateAccessor (método)"
ms.assetid: 594c8d6d-b49a-4818-a9a5-81c8115d4e42
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CManualAccessor::CreateAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigna memoria para las estructuras de enlace de columna e inicializa los miembros de datos de columna.  
  
## Sintaxis  
  
```  
  
      HRESULT CreateAccessor(   
   int nBindEntries,   
   void* pBuffer,   
   DBLENGTH nBufferSize    
) throw( );  
```  
  
#### Parámetros  
 `nBindEntries`  
 \[in\] Número de columnas.  Este número debe coincidir con el número de llamadas a la función de [CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) .  
  
 `pBuffer`  
 \[in\] Un puntero al búfer donde se almacenan las columnas de salida.  
  
 `nBufferSize`  
 \[in\] El tamaño del búfer en bytes.  
  
## Valor devuelto  
 Uno de los valores estándar de `HRESULT` .  
  
## Comentarios  
 Llame a esta función antes de llamar a la función de `CManualAccessor::AddBindEntry` .  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CManualAccessor \(Clase\)](../../data/oledb/cmanualaccessor-class.md)   
 [Ejemplo de DBViewer](../../top/visual-cpp-samples.md)