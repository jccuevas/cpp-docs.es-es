---
title: "Registry Entries | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Registro, application IDs"
  - "Registro, ATL services entries"
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Registry Entries
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

DCOM introduce el concepto de id. de la aplicación \(AppIDs\), que agrupan las opciones de configuración para uno o más objetos de DCOM en una ubicación centralizada en el registro.  Especifica un AppID indicando su valor en el AppID denominado valor bajo el CLSID del objeto.  
  
 De forma predeterminada, un servicio ATL\-generado utiliza su CLSID un GUID para el AppID.  En `HKEY_CLASSES_ROOT\AppID`, puede especificar entradas DCOM\-específicas.  inicialmente, dos entradas existen:  
  
-   `LocalService`, con un valor igual al nombre del servicio.  Si existe este valor, se utiliza en lugar de la clave de `LocalServer32` bajo el CLSID.  
  
-   `ServiceParameters`, con un valor igual a `–Service`.  Este valor especifica los parámetros que se pasarán al servicio cuando se inician.  Observe que estos parámetros se pasan a la función de `ServiceMain` de servicio, no `WinMain`.  
  
 Cualquier servicio de DCOM también necesita crear otra clave en `HKEY_CLASSES_ROOT\AppID`.  Esta clave es igual al nombre del archivo EXE y actúa como referencia cruzada, como contiene un valor AppID que apunta a las entradas de AppID.  
  
## Vea también  
 [Servicios](../atl/atl-services.md)