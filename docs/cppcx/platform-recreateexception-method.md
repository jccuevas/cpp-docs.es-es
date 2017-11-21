---
title: "Platform:: recreateexception (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::Exception
dev_langs: C++
helpviewer_keywords: Platform::Exception Class
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: e617d85c17db3c1e3cccb64786dfe7bfcfb9b1e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="platformrecreateexception-method"></a>Platform::ReCreateException (Método)
Este método es para uso interno únicamente y no se ha diseñado para el código del usuario. Utilice el método Exception:: CreateException en su lugar.

## <a name="syntax"></a>Sintaxis

```cpp
static Exception^ ReCreateException(int hr)
```

### <a name="parameters"></a>Parámetros
`hr`

### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Devuelve un nuevo Platform::Exception^, según el HRESULT especificado.

