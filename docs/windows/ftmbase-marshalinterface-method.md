---
title: MarshalInterface (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- MarshalInterface method
ms.assetid: fc8421b4-06e4-4925-b908-c285fe4790d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ff0c1a5e41dfe46f2d88aeeb3093dbc9ee4d4005
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570062"
---
# <a name="ftmbasemarshalinterface-method"></a>FtmBase::MarshalInterface (Método)
Escribe los datos necesarios para inicializar un objeto de proxy en algún proceso de cliente en una secuencia.  
  
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
  
### <a name="parameters"></a>Parámetros  
 *pStm*  
 Puntero a la secuencia que se usará durante la serialización.  
  
 *riid*  
 Referencia al identificador de la interfaz que se van a calcular. Esta interfaz debe derivarse de la `IUnknown` interfaz.  
  
 *PV*  
 Puntero al puntero de interfaz que se van a calcular; puede ser NULL si el llamador no tiene un puntero a la interfaz deseada.  
  
 *dwDestContext*  
 Contexto de destino donde se puede deserializar la interfaz especificada.  
  
 Especifique uno o más valores de enumeración MSHCTX.  
  
 Resolución de referencias puede ocurrir en otro contenedor del proceso actual (MSHCTX_INPROC) o en otro proceso en el mismo equipo que el proceso actual (MSHCTX_LOCAL).  
  
 *pvDestContext*  
 Reservado para uso futuro; debe ser cero.  
  
 *mshlflags*  
 Especifica si los datos se van a calcular están que se transmitan al proceso de cliente, el caso típico, o se escriben en una tabla global, donde se puede recuperar varios clientes.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK  
 El puntero de interfaz se serializó correctamente.  
  
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