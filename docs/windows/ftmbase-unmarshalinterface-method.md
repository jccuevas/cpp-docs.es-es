---
title: UnmarshalInterface (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- UnmarshalInterface method
ms.assetid: 6850a621-e9a6-4001-bc1e-bd5d1b121adc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ef462ae884aad4160ffbae1883485ac7e06d3aa5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610706"
---
# <a name="ftmbaseunmarshalinterface-method"></a>FtmBase::UnmarshalInterface (Método)

Inicializa a un proxy recién creado y devuelve un puntero de interfaz a ese proxy.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>Parámetros

*pStm*  
Puntero a la secuencia desde la que se puede deserializar el puntero de interfaz.

*riid*  
Referencia al identificador de la interfaz que puede deserializar.

*PPV*  
Cuando finalice esta operación, la dirección de una variable de puntero que recibe el puntero de interfaz solicitado en *riid*. Si esta operación se realiza correctamente, **ppv* contiene el puntero de interfaz solicitada de la interfaz que puede deserializar.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_NOINTERFACE o E_FAIL.

## <a name="requirements"></a>Requisitos

**Encabezado:** ftm.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[FtmBase (clase)](../windows/ftmbase-class.md)