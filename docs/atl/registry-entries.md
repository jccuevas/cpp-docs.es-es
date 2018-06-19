---
title: Entradas del registro (ATL) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac8e202fc2fc3d58e2d57a9fbfa15264d9fd310e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359734"
---
# <a name="registry-entries"></a>Entradas del Registro
DCOM presentó el concepto de Id. de aplicación (AppID), que agrupa las opciones de configuración de uno o más objetos DCOM en una ubicación centralizada en el registro. Para especificar un AppID, indique su valor en el AppID denominado valor bajo el CLSID del objeto.  
  
 De forma predeterminada, un servicio generado con ATL utiliza su CLSID como el GUID para su AppID. En `HKEY_CLASSES_ROOT\AppID`, puede especificar entradas específicas de DCOM. En principio, existen dos entradas:  
  
-   `LocalService`, con un valor igual al nombre del servicio. Si este valor no existe, se utiliza en lugar de la `LocalServer32` clave bajo el CLSID.  
  
-   `ServiceParameters`, con un valor igual a `-Service`. Este valor especifica parámetros que se pasarán al servicio cuando se inicie. Tenga en cuenta que estos parámetros se pasan al servicio `ServiceMain` funcione, no `WinMain`.  
  
 Cualquier servicio DCOM también debe crear otra clave bajo `HKEY_CLASSES_ROOT\AppID`. Esta clave es igual que el nombre del archivo EXE y actúa como una referencia cruzada, ya que contiene un valor AppID que apunta a las entradas AppID.  
  
## <a name="see-also"></a>Vea también  
 [Servicios](../atl/atl-services.md)

