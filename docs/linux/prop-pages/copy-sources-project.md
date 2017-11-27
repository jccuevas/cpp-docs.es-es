---
title: "Propiedades del proyecto Copiar orígenes (C++ para Linux) | Microsoft Docs"
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
author: mikeblome
ms.author: mblome
manager: ghogen
f1_keywords: VC.Project.VCConfiguration.BuildLogFile
ms.openlocfilehash: d552ef6bd5106b3db0e30214d8fbc144b9aa00eb
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="copy-sources-project-properties-linux-c"></a>Propiedades del proyecto Copiar orígenes (C++ para Linux)
Las propiedades establecidas en esta página de propiedades se aplican a todos los archivos del proyecto, excepto a aquellos cuyas propiedades de nivel de archivo están establecidas.

Propiedad | Descripción
--- | ---
Orígenes para copiar | Especifica los orígenes que deben copiarse en el sistema remoto. Si se cambia esta lista, podría modificar o afectar de alguna manera a la estructura de directorios donde se copian los archivos en el sistema remoto.
Copiar orígenes | Especifica si deben copiarse los orígenes en el sistema remoto.
Más orígenes para copiar | Especifica otros orígenes que deben copiarse en el sistema remoto. También se puede proporcionar la lista en forma de pares de asignaciones de local a remoto usando esta sintaxis: rutaDeAccesoLocalCompleta1:=rutaDeAccesoRemotaCompleta1;rutaDeAccesoLocalCompleta2:=rutaDeAccesoRemotaCompleta2, donde un archivo local se puede copiar en la ubicación remota especificada del sistema remoto.
