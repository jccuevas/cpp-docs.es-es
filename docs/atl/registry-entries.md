---
title: Entradas del registro (ATL) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 013a5827af630e8190e622940c1fd3872a46a5d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="registry-entries"></a>Entradas del Registro
DCOM presentó el concepto de Id. de aplicación (AppID), que agrupa las opciones de configuración de uno o más objetos DCOM en una ubicación centralizada en el registro. Para especificar un AppID, indique su valor en el AppID denominado valor bajo el CLSID del objeto.  
  
 De forma predeterminada, un servicio generado con ATL utiliza su CLSID como el GUID para su AppID. En `HKEY_CLASSES_ROOT\AppID`, puede especificar entradas específicas de DCOM. En principio, existen dos entradas:  
  
-   `LocalService`, con un valor igual al nombre del servicio. Si este valor no existe, se utiliza en lugar de la `LocalServer32` clave bajo el CLSID.  
  
-   `ServiceParameters`, con un valor igual a `-Service`. Este valor especifica parámetros que se pasarán al servicio cuando se inicie. Tenga en cuenta que estos parámetros se pasan al servicio `ServiceMain` funcione, no `WinMain`.  
  
 Cualquier servicio DCOM también debe crear otra clave bajo `HKEY_CLASSES_ROOT\AppID`. Esta clave es igual que el nombre del archivo EXE y actúa como una referencia cruzada, ya que contiene un valor AppID que apunta a las entradas AppID.  
  
## <a name="see-also"></a>Vea también  
 [Servicios de](../atl/atl-services.md)

