---
title: "Asistente para agregar funciones miembro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.function.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para agregar funciones miembro [C++]"
ms.assetid: 13b6defc-faa6-4d57-83db-9dd854cbea3d
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Asistente para agregar funciones miembro
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este asistente agrega la declaración de una función miembro al archivo de encabezado y una implementación de función miembro auxiliar al archivo de implementación de la clase seleccionada.  
  
 Una vez agregada la función miembro por medio del asistente, puede editar el código en el entorno de desarrollo.  
  
 **Tipo de valor devuelto**  
 Define el tipo de valor devuelto por la función miembro que se agrega.  Puede suministrar su propio tipo de valor devuelto o bien seleccionar uno en la lista de tipos disponibles.  Para obtener información acerca de los tipos, vea [Tipos fundamentales](../cpp/fundamental-types-cpp.md).  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned int`|  
|**double**|**long**|`unsigned long`|  
|**float**|**short**|`void`|  
|`HRESULT`|`unsigned char`||  
  
 **Nombre de la función**  
 Define el nombre de la función miembro que se agrega.  
  
 **Tipo de parámetro**  
 Define el tipo de parámetro que se agrega para la función miembro, si ésta acepta parámetros.  Puede suministrar su propio tipo de parámetro o bien seleccionar uno en la lista de tipos disponibles.  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned char`|  
|**double**|**long**|`unsigned int`|  
|**float**|**short**|`unsigned long`|  
  
 **Nombre de parámetro**  
 Define el nombre de un parámetro que se agrega a la función miembro, si ésta acepta parámetros.  
  
 **Lista de parámetros**  
 Muestra una lista de los parámetros que se han agregado a la función miembro.  Para agregar un parámetro a la lista, suministre un tipo y un nombre en los cuadros **Tipo de parámetro** y **Nombre de parámetro** y haga clic en **Agregar**.  Para quitar un parámetro de la lista, selecciónelo y haga clic en **Quitar**.  
  
 **Acceso**  
 Define el acceso a la función miembro.  Los modificadores de acceso son palabras clave que especifican el acceso que tienen otras clases a la función miembro.  Vea [Control de acceso a miembros](../cpp/member-access-control-cpp.md) para obtener más información sobre cómo especificar el acceso.  El nivel de acceso predeterminado de una función miembro es **public**.  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
 Compruebe si la nueva función miembro es estática o virtual, y si es inline o pura.  Si define la función miembro como pura, estará activada la casilla `Virtual`, pero la casilla **Inline** no estará disponible.  El valor predeterminado es una función miembro no estática y no virtual.  
  
|Opción|Descripción|  
|------------|-----------------|  
|[Static](../misc/static-cpp.md)|Especifica que la función se comporta como una función global a la que se puede llamar desde fuera de la clase, incluso sin configurar la instancia de la clase.  La función miembro no tiene acceso a miembros no estáticos.  Una función miembro especificada como `Static` no puede ser virtual.|  
|[Virtual](../cpp/virtual-cpp.md)|Asegura que se llama a la función miembro correcta para un objeto, con independencia de la expresión utilizada para llamarla.  Una función miembro especificada como `Virtual` no puede ser estática.|  
|**Pure**|Indica que no se suministra la implementación de la función miembro virtual que se declara; por lo tanto, **Pure** sólo puede especificarse en funciones miembro virtuales.  Para obtener más información, vea [Sintaxis de declaración de miembros de clase](../misc/class-member-declaration-syntax.md).<br /><br /> Una clase que contiene por lo menos una función miembro pura virtual se considera una clase abstracta.  Las clases derivadas de la clase abstracta deben implementar la función miembro virtual pura o, de lo contrario, también son clases abstractas.|  
|[En línea](../cpp/inline-functions-cpp.md)|Indica al compilador que inserte una copia del cuerpo de la función miembro en cada lugar donde se llame a la función.  Una función miembro especificada como **Inline** no puede ser pura.|  
  
 **Archivo .cpp**  
 Define la ubicación del archivo donde está escrita la implementación de la función miembro auxiliar.  De forma predeterminada, se escribe en el archivo .cpp de la clase a la que se agrega la función miembro.  Puede cambiar el nombre del archivo si hace clic en el botón de puntos suspensivos.  La implementación de la función miembro se agrega al contenido del archivo seleccionado.  
  
 **Comentarios**  
 Proporciona un comentario en el archivo de encabezado de la función miembro.  
  
 **Firma de la función**  
 Muestra la función miembro tal como aparece en el código cuando se hace clic en **Finalizar**.  El texto no se puede editar en este cuadro.  Para cambiar la función miembro, modifique los cuadros apropiados en el asistente.  
  
## Vea también  
 [Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)