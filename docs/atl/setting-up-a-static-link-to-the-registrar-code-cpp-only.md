---
title: Configurar un vínculo estático al código del registrador (sólo en C++) | Documentos de Microsoft
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
ms.openlocfilehash: dca93c8f0fcae578700a9d9970977179fbd142d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360193"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Cómo configurar un vínculo estático al código del registrador (sólo en C++)
Los clientes C++ pueden crear un vínculo estático al código del registrador. La vinculación estática de analizador del registrador agrega aproximadamente 5 KB a una versión de lanzamiento.  
  
 La manera más sencilla de configurar la vinculación estática, se da por supuesto que ha especificado [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) en la declaración del objeto. (Esta es la especificación de manera predeterminada utilizada por ATL.)  
  
### <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Para crear un vínculo estático mediante DECLARE_REGISTRY_RESOURCEID:  
  
1.  Especifique [/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY` en lugar de /D **_ATL_DLL**.  
  
2.  Vuelva a compilar.  
  
## <a name="see-also"></a>Vea también  
 [Componente de registro (registrador)](../atl/atl-registry-component-registrar.md)

