---
title: "Activaci&#243;n: Verbos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "activación [C++], verbos"
  - "editar verbo"
  - "OLE [C++], activación"
  - "OLE [C++], editar"
  - "activación de direcciones OLE"
  - "verbo principal"
  - "verbos"
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Activaci&#243;n: Verbos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica el rol principal y verbos secundarios sonar en OLE [activación](../mfc/activation-cpp.md).  
  
 Normalmente, haga doble clic en un elemento incrustado permite que el usuario lo edite.  Sin embargo, algunos elementos no se comportan de esta manera.  Por ejemplo, hacer doble clic en un elemento creado con la aplicación de grabadora de sonidos no abre el servidor en una ventana independiente; en su lugar, reproduce el sonido.  
  
 La razón de esta diferencia de comportamiento es que los elementos de la grabadora de sonidos tienen otro “verb primario”. El verbo primario es la acción realizada cuando el usuario hace doble clic en un elemento.  Para la mayoría de los tipos de elementos de OLE, el verbo primario es la edición, que inicia el servidor que creó el elemento.  Para algunos tipos de elementos, como elementos de grabadora de sonidos, el verbo primario es juego.  
  
 Muchos tipos de elementos de OLE solo admiten un verbo, y la edición es la más normal.  Sin embargo, algunos tipos de elementos admiten verbos.  Por ejemplo, edición de compatibilidad de los elementos de la grabadora de sonidos como verbo secundario.  
  
 Otro verbo utilizado con frecuencia está abierto.  El verbo abierto es idéntico a la edición, a menos que la aplicación de servidor se inicia en una ventana independiente.  Este verbo se debe utilizar cuando la aplicación contenedora o la aplicación de servidor no admite la activación en contexto.  
  
 Cualquier verbo distinto del verbo principal se debe invocar a través de un comando de submenú cuando se selecciona el elemento.  Este submenú contiene todos los verbos admitidos por el elemento y se tiene acceso normalmente mediante el comando de **objeto***typename*en el menú de **edición** .  Para obtener información sobre el comando de **objeto***typename*, vea el artículo [Menús y recursos: Adiciones de contenedor](../mfc/menus-and-resources-container-additions.md).  
  
 Los verbos que una aplicación de servidor admite se enumeran en la base de datos del registro de Windows.  Si la aplicación servidor se crea con la biblioteca Microsoft Foundation Class, automáticamente se registrarán todos los verbos cuando se inician al servidor.  Si no, debe registrarlos durante la fase de inicialización de la aplicación de servidor.  Para obtener más información, vea el artículo [Registro](../mfc/registration.md).  
  
## Vea también  
 [Activación](../mfc/activation-cpp.md)   
 [Contenedores](../mfc/containers.md)   
 [Servidores](../mfc/servers.md)