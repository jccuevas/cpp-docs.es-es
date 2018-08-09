---
title: GetMarshalSizeMax (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
dev_langs:
- C++
helpviewer_keywords:
- GetMarshalSizeMax method
ms.assetid: b416b1bf-c73e-45d5-abb8-04921c1a0c94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c7976d0ea22a0bf6f59b020f892d407c4721b9a7
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652362"
---
# <a name="ftmbasegetmarshalsizemax-method"></a>FtmBase::GetMarshalSizeMax (Método)
Obtenga el límite superior en el número de bytes necesarios para serializar el puntero de interfaz especificado en el objeto especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
STDMETHODIMP GetMarshalSizeMax(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out DWORD *pSize  
) override;  
```  
  
### <a name="parameters"></a>Parámetros  
 *riid*  
 Referencia al identificador de la interfaz que se van a calcular.  
  
 *PV*  
 Puntero de interfaz se van a calcular; puede ser NULL.  
  
 *dwDestContext*  
 Contexto de destino donde se puede deserializar la interfaz especificada.  
  
 Especifique uno o más valores de enumeración MSHCTX.  
  
 Actualmente, la resolución de referencias puede producirse en otro contenedor del proceso actual (MSHCTX_INPROC) o en otro proceso en el mismo equipo que el proceso actual (MSHCTX_LOCAL).  
  
 *pvDestContext*  
 Reservado para uso futuro; debe ser NULL.  
  
 *mshlflags*  
 Marca que indica si los datos se van a calcular están que se transmitan al proceso de cliente, el caso típico, o se escriben en una tabla global, donde se puede recuperar varios clientes. Especifique uno o más valores de enumeración MSHLFLAGS.  
  
 *pSize*  
 Cuando se completa esta operación, el puntero para el límite superior de la cantidad de datos se escriban en la secuencia de serialización.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, E_FAIL o E_NOINTERFACE.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ftm.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [FtmBase (clase)](../windows/ftmbase-class.md)