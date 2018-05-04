---
title: Rutas de búsqueda en reglas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- search paths in NMAKE inference rules
- inference rules in NMAKE
- rules, inference
ms.assetid: 38feded6-536d-425d-bf40-fff3173a5506
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25127377f20de3cb7c7b55e275692eefbf077067
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="search-paths-in-rules"></a>Rutas de búsqueda en reglas
```  
{frompath}.fromext{topath}.toext:  
   commands  
```  
  
## <a name="remarks"></a>Comentarios  
 Una regla de inferencia se aplica a una dependencia sólo si las rutas de acceso especificadas en la dependencia exactamente coinciden con las rutas de acceso de la regla de inferencia. Especifique el directorio del dependiente en *frompath* y el directorio de destino en *topath*; no se permiten espacios. Especifique solo una ruta de acceso para cada extensión. Una ruta de acceso en una extensión requiere una ruta de acceso en el otro. Para especificar el directorio actual, use un punto (.) o llaves vacías ({}). Las macros pueden representar *frompath* y *topath*; que se invoquen durante el preprocesamiento.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="code"></a>Código  
  
```  
{dbi\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUDBI) $<  
  
{ilstore\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $<  
  
{misc\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUPDB) $<  
  
{misc\}.c{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $<  
  
{msf\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $<  
  
{bsc\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUPDB) $<  
  
{mre\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUPDB) $<  
  
{namesrvr\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUPDB) $<  
  
{src\cvr\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $<  
```  
  
## <a name="see-also"></a>Vea también  
 [Definición de una regla](../build/defining-a-rule.md)