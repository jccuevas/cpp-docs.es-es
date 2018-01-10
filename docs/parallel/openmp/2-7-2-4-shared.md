---
title: 2.7.2.4 compartidos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4320a3df64d8056cf1c8657acc78281f56cd1c85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="2724-shared"></a>2.7.2.4 shared
Esta cláusula comparte las variables que aparecen en la *lista de variables* entre todos los subprocesos en un equipo. Todos los subprocesos dentro de un equipo obtener acceso a la misma área de almacenamiento para **compartido** variables.  
  
 La sintaxis de la **compartido** cláusula es como sigue:  
  
```  
shared(variable-list)  
```