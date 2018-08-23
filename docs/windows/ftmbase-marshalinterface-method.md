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
ms.openlocfilehash: a95521123a87a6ae68ce9f923779c1a6ceda4ccf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599716"
---
# <a name="ftmbasemarshalinterface-method"></a>FtmBase::MarshalInterface (Método)

Escribe los datos necesarios para inicializar un objeto de proxy en algún proceso de cliente en una secuencia.

## <a name="syntax"></a>Sintaxis

```cpp
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

S_OK el puntero de interfaz se serializó correctamente.

E_NOINTERFACE no se admite la interfaz especificada.

STG_E_MEDIUMFULL la secuencia está lleno.

No se pudo E_FAIL la operación.

## <a name="requirements"></a>Requisitos

**Encabezado:** ftm.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[FtmBase (clase)](../windows/ftmbase-class.md)