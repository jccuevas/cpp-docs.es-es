---
title: "Configurar un vínculo estático al código del registrador (sólo en C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b8eb77bc6f99ab6b7d8ca9d51f1a7a8549d8f0c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Cómo configurar un vínculo estático al código del registrador (sólo en C++)
Los clientes C++ pueden crear un vínculo estático al código del registrador. La vinculación estática de analizador del registrador agrega aproximadamente 5 KB a una versión de lanzamiento.  
  
 La manera más sencilla de configurar la vinculación estática, se da por supuesto que ha especificado [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) en la declaración del objeto. (Esta es la especificación de manera predeterminada utilizada por ATL.)  
  
### <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Para crear un vínculo estático mediante DECLARE_REGISTRY_RESOURCEID:  
  
1.  Especifique [/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY` en lugar de /D**_ATL_DLL**.  
  
2.  Vuelva a compilar.  
  
## <a name="see-also"></a>Vea también  
 [Componente de registro (registrador)](../atl/atl-registry-component-registrar.md)

