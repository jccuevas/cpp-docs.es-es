---
title: 'Ftmbase:: GetMarshalSizeMax (método) | Documentos de Microsoft'
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
ms.openlocfilehash: 5a298e63bc67dadf33a5e653d0eecf165a530d82
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="ftmbasegetmarshalsizemax-method"></a>FtmBase::GetMarshalSizeMax (Método)
Obtiene el límite superior en el número de bytes necesarios para serializar el puntero de interfaz especificado en el objeto especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `riid`  
 Referencia al identificador de la interfaz que se van a calcular.  
  
 `pv`  
 Puntero de interfaz que se van a calcular; puede ser NULL.  
  
 `dwDestContext`  
 Contexto de destino donde se puede deserializar la interfaz especificada.  
  
 Especifique uno o varios valores de enumeración de MSHCTX.  
  
 Actualmente, la resolución de referencias puede producirse en otro contenedor del proceso actual (MSHCTX_INPROC) o en otro proceso en el mismo equipo que el proceso actual (MSHCTX_LOCAL).  
  
 `pvDestContext`  
 Reservado para uso futuro; debe ser NULL.  
  
 `mshlflags`  
 Marca que indica si los datos que se van a calcular transmitirse hacia el proceso del cliente, el caso típico, o se escriben en una tabla global, donde se puede recuperar mediante varios clientes. Especifique uno o varios valores de enumeración de MSHLFLAGS.  
  
 `pSize`  
 Cuando se completa esta operación, puntero para el límite superior de la cantidad de datos se escriban en la secuencia de serialización.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, E_FAIL o E_NOINTERFACE.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ftm.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [FtmBase (clase)](../windows/ftmbase-class.md)