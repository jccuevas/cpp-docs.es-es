---
title: "Ftmbase:: MarshalInterface (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: ftm/Microsoft::WRL::FtmBase::MarshalInterface
dev_langs: C++
helpviewer_keywords: MarshalInterface method
ms.assetid: fc8421b4-06e4-4925-b908-c285fe4790d2
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9df1e5d7559b434c1af0f1feff3b73b8141a8865
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ftmbasemarshalinterface-method"></a>FtmBase::MarshalInterface (Método)
Escribe en una secuencia los datos necesarios para inicializar un objeto de proxy en algún proceso de cliente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDMETHODIMP MarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags  
) override;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStm`  
 Puntero a la secuencia que se usará durante la serialización.  
  
 `riid`  
 Referencia al identificador de la interfaz que se van a calcular. Esta interfaz debe derivarse de la interfaz IUnknown.  
  
 `pv`  
 Puntero al puntero de interfaz que se van a calcular; puede ser NULL si el llamador no tiene un puntero a la interfaz deseada.  
  
 `dwDestContext`  
 Contexto de destino donde se puede deserializar la interfaz especificada.  
  
 Especifique uno o varios valores de enumeración de MSHCTX.  
  
 Puede producirse la resolución de referencias en otro contenedor del proceso actual (MSHCTX_INPROC) o en otro proceso en el mismo equipo que el proceso actual (MSHCTX_LOCAL).  
  
 `pvDestContext`  
 Reservado para uso futuro; debe ser cero.  
  
 `mshlflags`  
 Especifica si los datos que se van a calcular transmitirse hacia el proceso del cliente, el caso típico, o se escriben en una tabla global, donde se puede recuperar mediante varios clientes.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK  
 El puntero de interfaz se ha convertido correctamente.  
  
 E_NOINTERFACE  
 No se admite la interfaz especificada.  
  
 STG_E_MEDIUMFULL  
 La secuencia está lleno.  
  
 E_FAIL  
 Error en la operación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ftm.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [FtmBase (clase)](../windows/ftmbase-class.md)