---
title: Rutas de búsqueda en reglas
ms.date: 11/04/2016
helpviewer_keywords:
- search paths in NMAKE inference rules
- inference rules in NMAKE
- rules, inference
ms.assetid: 38feded6-536d-425d-bf40-fff3173a5506
ms.openlocfilehash: eab6e9d32940aaf5729ce82c4e8258a3a3132208
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827754"
---
# <a name="search-paths-in-rules"></a>Rutas de búsqueda en reglas

```
{frompath}.fromext{topath}.toext:
   commands
```

## <a name="remarks"></a>Comentarios

Una regla de inferencia se aplica a una dependencia sólo si las rutas especificadas en la dependencia exactamente coinciden con las rutas de acceso de la regla de inferencia. Especifique el directorio del dependiente en *frompath* y el directorio de destino en *topath*; no se permiten espacios. Especifique una ruta única para cada extensión. Una ruta de acceso en una extensión requiere una ruta de acceso en el otro. Para especificar el directorio actual, use un punto (.) o llaves vacías ({}). Las macros pueden representar *frompath* y *topath*; se invocan durante el preprocesamiento.

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

[Definición de una regla](defining-a-rule.md)
