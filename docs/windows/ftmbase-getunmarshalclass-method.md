---
title: "FtmBase::GetUnmarshalClass (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetUnmarshalClass (método)"
ms.assetid: 535fc539-5b97-4967-b158-f7568f13d341
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FtmBase::GetUnmarshalClass (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene el CLSID que utiliza COM para encontrar un archivo DLL que contiene el código para el proxy correspondiente.  COM carga esta DLL para crear una instancia no inicializada del proxy.  
  
## Sintaxis  
  
```  
STDMETHODIMP GetUnmarshalClass(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out CLSID *pCid  
) override;  
```  
  
#### Parámetros  
 `riid`  
 Referencia al identificador de interfaz que se formará.  
  
 `pv`  
 Puntero a la interfaz que se formará; puede ser NULL si el llamador no tiene un puntero a la interfaz deseada.  
  
 `dwDestContext`  
 Contexto de destino donde se unmarshaled la interfaz especificada.  
  
 Especifique uno o más valores de enumeración de MSHCTX.  
  
 Unmarshaling puede aparecer en otro apartamento del proceso actual \(MSHCTX\_INPROC\) o en otro proceso en el mismo equipo que el proceso actual \(MSHCTX\_LOCAL\).  
  
 `pvDestContext`  
 Reservado para uso futuro; debe ser NULL.  
  
 `mshlflags`  
 Cuando esta operación finaliza, puntero a CLSID que se utilizará para crear un proxy en el proceso del cliente.  
  
 `pCid`  
  
## Valor devuelto  
 S\_OK si correctamente; si no, S\_FALSE.  
  
## Requisitos  
 **Encabezado:** ftm.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [FtmBase \(Clase\)](../windows/ftmbase-class.md)