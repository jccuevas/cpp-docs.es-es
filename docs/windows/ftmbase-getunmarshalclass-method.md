---
title: GetUnmarshalClass (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
dev_langs:
- C++
helpviewer_keywords:
- GetUnmarshalClass method
ms.assetid: 535fc539-5b97-4967-b158-f7568f13d341
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c76c2d75f3d8c2e872b29d9ecf07841c99027713
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599508"
---
# <a name="ftmbasegetunmarshalclass-method"></a>FtmBase::GetUnmarshalClass (Método)

Obtiene el CLSID que COM que se utiliza para localizar el archivo DLL que contiene el código para el proxy correspondiente. COM carga este archivo DLL para crear una instancia del proxy no inicializada.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHODIMP GetUnmarshalClass(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out CLSID *pCid
) override;
```

### <a name="parameters"></a>Parámetros

*riid*  
Referencia al identificador de la interfaz que se van a calcular.

*PV*  
Puntero a la interfaz que se van a calcular; puede ser NULL si el llamador no tiene un puntero a la interfaz deseada.

*dwDestContext*  
Contexto de destino donde se puede deserializar la interfaz especificada.

Especifique uno o más valores de enumeración MSHCTX.

Resolución de referencias puede producirse en otro contenedor del proceso actual (MSHCTX_INPROC) o en otro proceso en el mismo equipo que el proceso actual (MSHCTX_LOCAL).

*pvDestContext*  
Reservado para uso futuro; debe ser NULL.

*mshlflags*  
Cuando se completa esta operación, puntero al CLSID que se usará para crear un proxy en el proceso del cliente.

*pCid*

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, S_FALSE.

## <a name="requirements"></a>Requisitos

**Encabezado:** ftm.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[FtmBase (clase)](../windows/ftmbase-class.md)