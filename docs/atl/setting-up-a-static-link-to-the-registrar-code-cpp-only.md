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
ms.openlocfilehash: 3bde1d369ce5339f07ea36979ef50ddccb0d30d1
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860282"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Configurar un vínculo estático al código del registrador (solo C++)

Los clientes de C++ pueden crear un vínculo estático al código del registrador. Vinculación estática del analizador del registrador de, aproximadamente 5K agrega a una versión de lanzamiento.

La manera más sencilla de configurar la vinculación estática, se da por supuesto que ha especificado [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) en la declaración del objeto. (Esta es la especificación predeterminada que usa ATL.)

## <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Para crear un vínculo estático mediante DECLARE_REGISTRY_RESOURCEID:

1. Especificar [/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY` en lugar de /D **_ATL_DLL**.

1. Vuelva a compilar.

## <a name="see-also"></a>Vea también

[Componente de registro (registrador)](../atl/atl-registry-component-registrar.md)
