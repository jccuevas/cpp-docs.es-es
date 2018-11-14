---
title: Configurar un vínculo estático al código del registrador (solo C++)
ms.date: 11/04/2016
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: 11600b47abbbd247d099d871fce5e9d5d17d3cf4
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327894"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Configurar un vínculo estático al código del registrador (solo C++)

Los clientes de C++ pueden crear un vínculo estático al código del registrador. Vinculación estática del analizador del registrador de, aproximadamente 5K agrega a una versión de lanzamiento.

La manera más sencilla de configurar la vinculación estática, se da por supuesto que ha especificado [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) en la declaración del objeto. (Esta es la especificación predeterminada que usa ATL.)

## <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Para crear un vínculo estático mediante DECLARE_REGISTRY_RESOURCEID:

1. Especificar [/D](../build/reference/d-preprocessor-definitions.md)  **\_ATL\_estático\_registro** en lugar de **/D \_ATL\_DLL**.

1. Vuelva a compilar.

## <a name="see-also"></a>Vea también

[Componente de registro (registrador)](../atl/atl-registry-component-registrar.md)
