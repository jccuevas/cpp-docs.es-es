---
title: "CManualAccessor::AddParameterEntry | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CManualAccessor::AddParameterEntry"
  - "ATL.CManualAccessor.AddParameterEntry"
  - "CManualAccessor.AddParameterEntry"
  - "AddParameterEntry"
  - "ATL::CManualAccessor::AddParameterEntry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddParameterEntry (método)"
ms.assetid: 9048b164-052b-41b1-a861-227fc529e0b5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CManualAccessor::AddParameterEntry
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Agrega una entrada de parámetro a las estructuras de entrada de parámetros.  
  
## Sintaxis  
  
```  
  
      void AddParameterEntry(  
   DBORDINAL nOrdinal,  
   DBTYPE wType,  
   DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL,  
   DBPARAMIO eParamIO = DBPARAMIO_INPUT   
) throw ( );  
```  
  
#### Parámetros  
 Vea [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) en *la referencia del*programador.  
  
 `nOrdinal`  
 \[in\] Número del parámetro.  
  
 `wType`  
 \[in\] Tipo de datos.  
  
 `nColumnSize`  
 \[in\] Tamaño de la columna en bytes.  
  
 `pData`  
 \[in\] Un puntero a los datos de columna almacenados en el búfer.  
  
 `pLength`  
 \[in\] Un puntero a la longitud de campo, si es necesario.  
  
 `pStatus`  
 \[in\] Un puntero a la variable que se enlazará el estado de la columna, si es necesario.  
  
 *eParamIO*  
 \[in\] Especifica si el parámetro al que está asociado el enlace es una entrada, una entrada, o un parámetro de salida.  
  
## Comentarios  
 Para utilizar esta función, debe llamar primero a [CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CManualAccessor \(Clase\)](../../data/oledb/cmanualaccessor-class.md)   
 [CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)   
 [Ejemplo de DBViewer](../../top/visual-cpp-samples.md)