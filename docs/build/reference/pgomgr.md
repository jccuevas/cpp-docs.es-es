---
title: "pgomgr | Microsoft Docs"
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
  - "pgomgr (programa)"
  - "optimizaciones guiadas por perfiles, pgomgr"
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# pgomgr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Agrega los datos del perfil de uno o más archivos .pgc al archivo .pgd.  
  
## Sintaxis  
  
```  
pgomgr [options] pgcfiles pgdfile  
```  
  
#### Parámetros  
 `options`  
 Se pueden especificar las opciones siguientes para pgomgr:  
  
 **\/help**: Muestra las opciones de pgomgr disponibles \(abreviado para \/?\).  
  
 **\/clear**: Borra toda la información de perfil del archivo .pgd.  No se puede indicar un archivo .pgc cuando se especifica **\/clear**.  
  
 **\/detail**: Muestra estadísticas detalladas, incluyendo información de cobertura de gráficos de flujo.  
  
 **\/summary**: Muestra estadísticas por función.  
  
 **\/unique**: Cuando se utiliza con **\/summary**, muestra los nombres representativos de función.  La opción predeterminada, cuando no se utiliza \/unique, es que se muestren los nombres de función no representativos.  
  
 **\/merge**\[**:***n*\]**:** Agrega los datos de los archivos .pgc al archivo .pgd.  El parámetro opcional, *n*, le permite especificar que los datos se deben agregar *n* veces.  Por ejemplo, si normalmente un escenario se debería repetir 6 veces, se puede hacer una ejecución de prueba y agregarla al archivo .pgd seis veces con **pgomgr \/merge:6**.  
  
 `pgcfiles`  
 Uno o más archivos .pgc cuyos datos de perfil desea combinar en el archivo .pgd.  Puede especificar un solo archivo .pgc o varios.  Si no especifica ningún archivo .pgc, pgomgr combinará todos los archivos .pgc cuyos nombres de archivo coincidan con el del archivo .pgd.  
  
 `pgdfile`  
 El archivo .pgd en el que va a combinar los datos de los archivos .pgc.  
  
## Comentarios  
  
> [!NOTE]
>  Sólo puede iniciar esta herramienta desde el símbolo del sistema de [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)].  No puede iniciar desde una ventana del símbolo del sistema o desde el Explorador de archivos.  
  
## Ejemplo  
 En el ejemplo siguiente, se han borrado los datos de perfil del archivo .pgd.  
  
```  
pgomgr /clear myapp.pgd  
```  
  
 En el ejemplo siguiente, se han agregado los datos de perfil de myapp1.pgc al archivo .pgd 3 veces.  
  
```  
pgomgr /merge:3 myapp1.pgc myapp.pgd  
```  
  
 En el ejemplo siguiente, se agregan datos de perfil de todos los archivos myapp\#.pgc al archivo myapp.pgd.  
  
```  
pgomgr -merge myapp1.pgd  
```  
  
## Vea también  
 [Herramientas para la optimización basada en perfiles](../../build/reference/tools-for-manual-profile-guided-optimization.md)