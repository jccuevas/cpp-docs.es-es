---
title: "type_info (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "type_info"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clase type_info"
  - "type_info (clase)"
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# type_info (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase **type\_info** describe la información de tipo generada en el programa por el compilador.  Los objetos de esta clase almacenan de forma eficaz un puntero a un nombre para el tipo.  La clase **type\_info** también almacena un valor codificado adecuado para comparar dos tipos en cuanto a igualdad u orden de intercalación.  Las reglas de codificación y la secuencia de intercalación para tipos no se especifican y pueden diferir entre programas.  
  
 El archivo de encabezado \<`typeinfo>` debe incluirse para utilizar la clase **type\_info**.  La interfaz para la clase **type\_info** es:  
  
```  
class type_info {  
public:  
    virtual ~type_info();  
    size_t hash_code() const  
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;  
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;  
    _CRTIMP_PURE int before(const type_info& rhs) const;  
    _CRTIMP_PURE const char* name() const;  
    _CRTIMP_PURE const char* raw_name() const;  
};  
```  
  
 No puede crear instancias de objetos de la clase **type\_info** directamente porque la clase solo tiene un constructor de copias privado.  La única manera de crear un objeto **type\_info** \(temporal\) es utilizar el operador [typeid](../cpp/typeid-operator.md).  Como el operador de asignación también es privado, no puede copiar ni asignar objetos de la clase **type\_info**.  
  
 **type\_info::hash\_code** define una función hash adecuada para asignar valores de tipo **typeinfo** a una distribución de valores de índice.  
  
 Los operadores `==` y `!=` se pueden utilizar para comparar la igualdad y la desigualdad con otros objetos **type\_info**, respectivamente.  
  
 No hay ningún vínculo entre el orden de intercalación de tipos y las relaciones de herencia.  Utilice la función miembro **type\_info::before** para determinar la secuencia de intercalación de tipos.  No hay ninguna garantía de que **type\_info::before** produzca el mismo resultado en programas diferentes o incluso ejecuciones diferentes del mismo programa.  De esta manera, **type\_info::before** es similar al operador **\(&\)** de dirección.  
  
 La función miembro **type\_info::name** devuelve **const char\*** a una cadena finalizada en null que representa el nombre legible del tipo.  La memoria a la que se señala se almacena en caché y nunca debe desasignarse directamente.  
  
 La función miembro **type\_info::raw\_name** devuelve **const char\*** a una cadena finalizada en null que representa el nombre representativo del tipo de objeto.  El nombre se almacena realmente en forma representativa para ahorrar espacio.  Por consiguiente, esta función es más rápida que **type\_info::name** porque no necesita anular la aplicación de nombre representativo.  La cadena devuelta por la función **type\_info::raw\_name** es útil en operaciones de comparación pero no es legible.  Si necesita una cadena legible, utilice en su lugar la función **type\_info::name**.  
  
 La información de tipo se genera para las clases polimórficas solo si se especifica la opción del compilador [\/GR \(Habilitar información de tipo en tiempo de ejecución\)](../build/reference/gr-enable-run-time-type-information.md).  
  
## Vea también  
 [Información de tipos en tiempo de ejecución](../cpp/run-time-type-information.md)