---
title: "FtmBase::GetMarshalSizeMax (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetMarshalSizeMax (método)"
ms.assetid: b416b1bf-c73e-45d5-abb8-04921c1a0c94
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# FtmBase::GetMarshalSizeMax (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene el límite superior en el número de bytes necesarios para formar el puntero de interfaz especificado en el objeto especificado.  
  
## Sintaxis  
  
```  
STDMETHODIMP GetMarshalSizeMax(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out DWORD *pSize  
) override;  
```  
  
#### Parámetros  
 `riid`  
 Referencia al identificador de interfaz que se formará.  
  
 `pv`  
 Puntero de interfaz que se formará; puede ser NULL.  
  
 `dwDestContext`  
 Contexto de destino donde se unmarshaled la interfaz especificada.  
  
 Especifique uno o más valores de enumeración de MSHCTX.  
  
 Actualmente, el unmarshaling puede aparecer en otro apartamento del proceso actual \(MSHCTX\_INPROC\) o en otro proceso en el mismo equipo que el proceso actual \(MSHCTX\_LOCAL\).  
  
 `pvDestContext`  
 Reservado para uso futuro; debe ser NULL.  
  
 `mshlflags`  
 Marcador que indica si los datos calcularse debe ser transmitido al proceso de cliente — el caso típico — o escribir en una tabla global, donde puede ser recuperada por varios clientes.  Especifique uno o más valores de enumeración de MSHLFLAGS.  
  
 `pSize`  
 Cuando esta operación finaliza, puntero al límite superior en la cantidad de datos que se van a escribir en la secuencia de cálculo de referencias.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, E\_FAIL o E\_NOINTERFACE.  
  
## Requisitos  
 **Encabezado:** ftm.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [FtmBase \(Clase\)](../windows/ftmbase-class.md)