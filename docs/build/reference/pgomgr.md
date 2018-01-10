---
title: pgomgr | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8cbb9a4f8b92a1cd495e1312c1aa8a8f77cefcd3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="pgomgr"></a>pgomgr
Agrega datos de perfil de uno o más archivos .pgc al archivo .pgd.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
pgomgr [options] pgcfiles pgdfile  
```  
  
#### <a name="parameters"></a>Parámetros  
 `options`  
 Pueden especificar las opciones siguientes para pgomgr:  
  
 **/ help:**muestra las opciones disponibles pgomgr (abreviatura de /?).  
  
 **/ Borrar:**hace que el archivo .pgd se va a borrar toda la información de perfil. No se puede especificar un .pgc archivo cuando **/borrar** se especifica.  
  
 **/ detail**: muestra estadísticas detalladas, incluida la información de cobertura de gráfico de flujo.  
  
 **/ summary**: muestra las estadísticas por función.  
  
 **/ único**: cuando se usa con **/summary**, nombres de función para mostrar representativos de causas.  El valor predeterminado, cuando / es único no se utiliza, es para que se muestren los nombres de función no representativo.  
  
 **/ merge**[**:***n*]**:**hace que los datos en el archivo .pgc o archivos que se agregarán al archivo .pgd.  El parámetro opcional,  *n* , permite especificar hat los datos debe agregarse  *n*  veces.  Por ejemplo, si un escenario normalmente se realizarían 6 veces, puede hacerlo una vez en una serie de pruebas y agregarlo al archivo .pgd seis veces con **pgomgr/Merge: 6**.  
  
 `pgcfiles`  
 Uno o más archivos .pgc cuyos datos de perfil que desea combinar en el archivo. pgd. Puede especificar un solo archivo .pgc o varios archivos .pgc. Si no especifica ningún archivo .pgc, pgomgr combinará todos los archivos .pgc cuyos nombres de archivo son los mismos que el archivo. pgd.  
  
 `pgdfile`  
 El archivo .pgd en el que se mezclan los datos desde el archivo .pgc o los archivos.  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Puede iniciar esta herramienta solo desde el símbolo del sistema de [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, el archivo .pgd se borró de datos de perfil.  
  
```  
pgomgr /clear myapp.pgd  
```  
  
 En el ejemplo siguiente, los datos de perfil de myapp1.pgc se agregan al archivo .pgd 3 veces.  
  
```  
pgomgr /merge:3 myapp1.pgc myapp.pgd  
```  
  
 En el ejemplo siguiente, se agregan datos de perfil de todos los archivos myapp # .pgc al archivo myapp.pgd.  
  
```  
pgomgr -merge myapp1.pgd  
```  
  
## <a name="see-also"></a>Vea también  
 [Herramientas para la optimización manual guiada por perfiles](../../build/reference/tools-for-manual-profile-guided-optimization.md)