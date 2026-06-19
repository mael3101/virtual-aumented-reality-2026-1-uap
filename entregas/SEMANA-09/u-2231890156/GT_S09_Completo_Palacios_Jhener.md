# Guía de Trabajo 09 — Diseño de Escenarios 3D
## ⚠️ VERSIÓN ESTUDIANTE

**Estudiante:** Palacios Vergaray Jhener Erick **Código:** 2231890156
**Fecha:** 18/06/2026 | **Puntuación total:** ____/20

---
**1.** ProBuilder en Unity permite:
- [ ] a) Importar modelos de Blender automáticamente
- [x] b) Crear geometría 3D directamente dentro del editor de Unity
- [ ] c) Generar texturas procedurales para cualquier objeto
- [ ] d) Compilar shaders personalizados para AR

**Explicación:**  
Permite modelar objetos básicos directamente dentro de Unity, facilitando la creación rápida de escenarios sin depender de herramientas externas.

---

**2.** En iluminación "Baked", la iluminación:
- [ ] a) Se calcula en tiempo real en cada frame
- [x] b) Se precalcula y se guarda en texturas (lightmaps) — cero costo en runtime
- [ ] c) Se descarga desde un servidor en la nube
- [ ] d) Solo funciona con luz ambiental, no con luces direccionales

**Explicación:**  
Al almacenarse previamente en lightmaps, la iluminación ya no necesita calcularse continuamente durante la ejecución de la aplicación.

---

**3.** "Static Batching" en Unity:
- [ ] a) Combina todos los objetos en una sola malla en tiempo real
- [x] b) Agrupa objetos estáticos con el mismo material en un solo draw call
- [ ] c) Reduce el número de polígonos de los objetos automáticamente
- [ ] d) Solo funciona con objetos instanciados desde Prefabs

**Explicación:**  
Esta técnica disminuye el trabajo de renderizado agrupando objetos estáticos similares, lo que mejora el rendimiento de la escena.

---

**4.** LOD Group significa:
- [ ] a) Layer Of Darkness — control de sombras por capa
- [x] b) Level Of Detail — cambia la complejidad del modelo según distancia
- [ ] c) List Of Draw calls — optimización de renderizado
- [ ] d) Load On Demand — carga objetos cuando son necesarios

**Explicación:**  
Reduce el consumo de recursos mostrando versiones simplificadas de los modelos cuando se encuentran lejos de la cámara.

---

**5.** Para AR en celular Android de gama media, ¿cuántos draw calls máximo se recomienda?
- [ ] a) ≤500 draw calls
- [ ] b) ≤250 draw calls
- [x] c) ≤100 draw calls
- [ ] d) No hay límite, el driver los gestiona automáticamente

**Explicación:**  
Mantener una cantidad reducida de draw calls ayuda a conservar una experiencia fluida y estable en dispositivos móviles.

---

**6.** Occlusion Culling en Unity:
- [ ] a) Reduce la resolución de texturas en tiempo real
- [x] b) Evita renderizar objetos que están ocultos detrás de otros
- [ ] c) Elimina triángulos duplicados de la malla
- [ ] d) Combina materiales similares en uno solo

**Explicación:**  
Evita procesar objetos que el usuario no puede observar, permitiendo aprovechar mejor los recursos disponibles.

---

### 3.1 (2 pt) Identifica los 3 problemas principales de rendimiento basándote en los valores.

| Valor | Problema | Impacto |
|-------|---------|---------|
| Draw Calls: 347 | Exceso de draw calls | Mayor carga para CPU y renderizado lento |
| Tris: 2.1M | Demasiados polígonos en la escena | Sobrecarga de GPU y menor rendimiento |
| FPS: 12 | Tasa de cuadros muy baja | Experiencia poco fluida y posible mareo en XR |

**Explicación:**  
Los indicadores muestran una escena poco optimizada, ya que existe una carga elevada tanto para la CPU como para la GPU, afectando directamente la fluidez.

---

### 3.2 (3 pt) Propón 3 técnicas de optimización específicas para mejorar esta escena. Para cada una, indica cómo la aplicarías.

| Técnica | Cómo aplicarla | Mejora esperada |
|---------|---------------|----------------|
| Static Batching | Marcar objetos estáticos con el mismo material como Static | Reducir draw calls |
| LOD Group | Crear versiones simplificadas de objetos lejanos | Reducir cantidad de triángulos renderizados |
| Occlusion Culling | Habilitar Occlusion Culling en paredes y estructuras | Evitar renderizar objetos ocultos |

**Explicación:**  
Las técnicas propuestas buscan reducir la complejidad visual y la cantidad de elementos procesados en cada frame para mejorar el rendimiento general.

---

### 4.1 (3 pt) Para el escenario de tu proyecto grupal, completa:

| Elemento | ¿Estático o dinámico? | Técnica de optimización | Material (descripción) |
|---------|----------------------|------------------------|----------------------|
| Placa madre | Estático | Static Batching | Material PBR con textura de circuito electrónico |
| CPU | Estático | Lightmap Baked | Material metálico con acabado brillante |
| Memoria RAM | Estático | GPU Instancing | Material plástico y metálico |
| Etiquetas informativas UI | Dinámico | Canvas optimizado | Material UI transparente con texto educativo |

**Explicación:**  
Los componentes físicos del hardware permanecen fijos durante la experiencia, mientras que los elementos informativos cambian según las acciones realizadas por el usuario.