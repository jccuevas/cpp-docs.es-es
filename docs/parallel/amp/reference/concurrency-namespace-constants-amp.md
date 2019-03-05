---
title: Constantes de espacio de nombres de simultaneidad (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::HLSL_MAX_NUM_BUFFERS
- amp/Concurrency::MODULENAME_MAX_LENGTH
ms.assetid: 13a8e8cd-2eec-4e60-a91d-5d271072747b
ms.openlocfilehash: c6cdaa36f481bd4a703981bfa1bc0617860b0917
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303340"
---
# <a name="concurrency-namespace-constants-amp"></a>Constantes de espacio de nombres de simultaneidad (AMP)

|||
|-|-|
|[HLSL_MAX_NUM_BUFFERS](#hlsl_max_num_buffers)|[MODULENAME_MAX_LENGTH](#modulename_max_length)|

##  <a name="hlsl_max_num_buffers"></a>  HLSL_MAX_NUM_BUFFERS Constant

El número máximo de búferes permitido por DirectX.

```
static const UINT HLSL_MAX_NUM_BUFFERS = 64 + 128;
```

##  <a name="modulename_max_length"></a>  MODULENAME_MAX_LENGTH (constante)

Almacena la longitud máxima del nombre del módulo. Este valor debe ser el mismo en el compilador y el tiempo de ejecución.

```
static const UINT MODULENAME_MAX_LENGTH = 1024;
```

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
