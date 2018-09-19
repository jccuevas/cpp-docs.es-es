---
title: Configurar un vínculo estático al código del registrador (solo C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a66ca33aa95ea6ffd59860cf0a55e51266ef5cb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757703"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Configurar un vínculo estático al código del registrador (solo C++)

Los clientes de C++ pueden crear un vínculo estático al código del registrador. Vinculación estática del analizador del registrador de, aproximadamente 5K agrega a una versión de lanzamiento.

La manera más sencilla de configurar la vinculación estática, se da por supuesto que ha especificado [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) en la declaración del objeto. (Esta es la especificación predeterminada que usa ATL.)

### <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Para crear un vínculo estático mediante DECLARE_REGISTRY_RESOURCEID:

1. Especificar [/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY` en lugar de /D **_ATL_DLL**.

2. Vuelva a compilar.

## <a name="see-also"></a>Vea también

[Componente de registro (registrador)](../atl/atl-registry-component-registrar.md)

