import * as THREE from 'three';
import { OrbitControls } from 'three/addons/controls/OrbitControls.js';

const BASE_URL = 'https://raw.githubusercontent.com/elbotnpc4-lab/Body/main/Data/';

const [nombresMusculos, infoMusculos, baseDatos] = await Promise.all([
    fetch(BASE_URL + 'nombres.json').then(r => r.json()),
    fetch(BASE_URL + 'musculos.json').then(r => r.json()),
    fetch(BASE_URL + 'ejercicios.json').then(r => r.json())
]);

const PROFUNDOS = [
    'transverso_abdominal', 'psoas_iliaco_izq', 'psoas_iliaco_der',
    'subescapular_izq', 'subescapular_der', 'oblicuo_int_izq', 'oblicuo_int_der',
    'gluteo_menor_izq', 'gluteo_menor_der', 'piriforme_izq', 'piriforme_der',
    'vastointermedio_izq', 'vastointermedio_der', 'popliteo_izq', 'popliteo_der',
    'intrinsecos_pie_izq', 'intrinsecos_pie_der', 'cuadrado_lumbar_izq', 'cuadrado_lumbar_der',
    'serrato_post_sup_izq', 'serrato_post_sup_der', 'serrato_post_inf_izq', 'serrato_post_inf_der',
    'redondo_menor_izq', 'redondo_menor_der', 'coracobraquial_izq', 'coracobraquial_der',
    'anconeo_izq', 'anconeo_der', 'espinoso_izq', 'espinoso_der',
    'intercostal_izq_0', 'intercostal_izq_1', 'intercostal_izq_2', 'intercostal_izq_3',
    'intercostal_der_0', 'intercostal_der_1', 'intercostal_der_2', 'intercostal_der_3',
    'largo_cuello_izq', 'largo_cuello_der', 'largo_cabeza_izq', 'largo_cabeza_der',
    'recto_ant_cabeza_izq', 'recto_ant_cabeza_der',
    'gemino_sup_izq', 'gemino_sup_der', 'gemino_inf_izq', 'gemino_inf_der',
    'cuadrado_femoral_izq', 'cuadrado_femoral_der',
    'pectineo_izq', 'pectineo_der', 'aductor_corto_izq', 'aductor_corto_der',
    'esplenio_izq', 'esplenio_der',
    'oblicuo_sup_cabeza_izq', 'oblicuo_sup_cabeza_der',
    'oblicuo_inf_cabeza_izq', 'oblicuo_inf_cabeza_der'
];

const ARTICULACIONES = [
    'hombro_izq', 'hombro_der', 'codo_izq', 'codo_der', 'muneca_izq', 'muneca_der',
    'cadera_izq', 'cadera_der', 'rodilla_izq', 'rodilla_der', 'tobillo_izq', 'tobillo_der',
    'columna_cervical', 'columna_toracica', 'columna_lumbar'
];

const ESTRUCTURAS = ['cabeza', 'cuello', 'occipital', 'mano_izq', 'mano_der', 'pie_izq', 'pie_der',
    'mano_izq_palma', 'mano_der_palma',
    'mano_izq_dedo_0', 'mano_izq_dedo_1', 'mano_izq_dedo_2', 'mano_izq_dedo_3',
    'mano_der_dedo_0', 'mano_der_dedo_1', 'mano_der_dedo_2', 'mano_der_dedo_3',
    'mano_izq_pulgar', 'mano_der_pulgar'];

const MUSCULOS_RELACIONADOS = {
    'largo_cuello_izq': ['Largo de la Cabeza', 'Recto Anterior de la Cabeza', 'Esternocleidomastoideo'],
    'largo_cuello_der': ['Largo de la Cabeza', 'Recto Anterior de la Cabeza', 'Esternocleidomastoideo'],
    'largo_cabeza_izq': ['Largo del Cuello', 'Recto Anterior de la Cabeza'],
    'largo_cabeza_der': ['Largo del Cuello', 'Recto Anterior de la Cabeza'],
    'recto_ant_cabeza_izq': ['Largo de la Cabeza', 'Largo del Cuello'],
    'recto_ant_cabeza_der': ['Largo de la Cabeza', 'Largo del Cuello'],
    'elevador_escapula_izq': ['Trapecio Superior', 'Romboides', 'Esternocleidomastoideo'],
    'elevador_escapula_der': ['Trapecio Superior', 'Romboides', 'Esternocleidomastoideo'],
    'coracobraquial_izq': ['Bíceps Cabeza Corta', 'Pectoral Mayor', 'Deltoides Anterior'],
    'coracobraquial_der': ['Bíceps Cabeza Corta', 'Pectoral Mayor', 'Deltoides Anterior'],
    'anconeo_izq': ['Tríceps Cabeza Lateral', 'Tríceps Cabeza Medial'],
    'anconeo_der': ['Tríceps Cabeza Lateral', 'Tríceps Cabeza Medial'],
    'iliocostal_izq': ['Longísimo', 'Espinoso', 'Cuadrado Lumbar'],
    'iliocostal_der': ['Longísimo', 'Espinoso', 'Cuadrado Lumbar'],
    'longisimo_izq': ['Iliocostal', 'Espinoso'],
    'longisimo_der': ['Iliocostal', 'Espinoso'],
    'espinoso_izq': ['Iliocostal', 'Longísimo'],
    'espinoso_der': ['Iliocostal', 'Longísimo'],
    'cuadriceps_recto_izq': ['Vasto Lateral', 'Vasto Medial', 'Vasto Intermedio', 'Sartorio'],
    'cuadriceps_recto_der': ['Vasto Lateral', 'Vasto Medial', 'Vasto Intermedio', 'Sartorio'],
    'vastolateral_izq': ['Recto Femoral', 'Vasto Medial', 'Vasto Intermedio'],
    'vastolateral_der': ['Recto Femoral', 'Vasto Medial', 'Vasto Intermedio'],
    'vastomedial_izq': ['Recto Femoral', 'Vasto Lateral', 'Vasto Intermedio'],
    'vastomedial_der': ['Recto Femoral', 'Vasto Lateral', 'Vasto Intermedio'],
    'vastointermedio_izq': ['Recto Femoral', 'Vasto Lateral', 'Vasto Medial'],
    'vastointermedio_der': ['Recto Femoral', 'Vasto Lateral', 'Vasto Medial'],
    'biceps_femoral_izq': ['Semitendinoso', 'Semimembranoso'],
    'biceps_femoral_der': ['Semitendinoso', 'Semimembranoso'],
    'semitendinoso_izq': ['Bíceps Femoral', 'Semimembranoso'],
    'semitendinoso_der': ['Bíceps Femoral', 'Semimembranoso'],
    'semimembranoso_izq': ['Bíceps Femoral', 'Semitendinoso'],
    'semimembranoso_der': ['Bíceps Femoral', 'Semitendinoso'],
    'gluteo_mayor_izq': ['Glúteo Medio', 'Glúteo Menor', 'Piriforme'],
    'gluteo_mayor_der': ['Glúteo Medio', 'Glúteo Menor', 'Piriforme'],
    'gluteo_med_izq': ['Glúteo Mayor', 'Glúteo Menor', 'Tensor Fascia Lata'],
    'gluteo_med_der': ['Glúteo Mayor', 'Glúteo Menor', 'Tensor Fascia Lata'],
    'biceps_corto_izq': ['Bíceps Cabeza Larga', 'Braquial', 'Coracobraquial'],
    'biceps_corto_der': ['Bíceps Cabeza Larga', 'Braquial', 'Coracobraquial'],
    'biceps_largo_izq': ['Bíceps Cabeza Corta', 'Braquial'],
    'biceps_largo_der': ['Bíceps Cabeza Corta', 'Braquial'],
    'triceps_largo_izq': ['Tríceps Cabeza Lateral', 'Tríceps Cabeza Medial', 'Ancóneo'],
    'triceps_largo_der': ['Tríceps Cabeza Lateral', 'Tríceps Cabeza Medial', 'Ancóneo'],
    'triceps_lat_izq': ['Tríceps Cabeza Larga', 'Tríceps Cabeza Medial', 'Ancóneo'],
    'triceps_lat_der': ['Tríceps Cabeza Larga', 'Tríceps Cabeza Medial', 'Ancóneo'],
    'triceps_med_izq': ['Tríceps Cabeza Larga', 'Tríceps Cabeza Lateral'],
    'triceps_med_der': ['Tríceps Cabeza Larga', 'Tríceps Cabeza Lateral'],
    'deltoides_ant_izq': ['Deltoides Lateral', 'Deltoides Posterior', 'Pectoral Mayor', 'Coracobraquial'],
    'deltoides_ant_der': ['Deltoides Lateral', 'Deltoides Posterior', 'Pectoral Mayor', 'Coracobraquial'],
    'deltoides_lat_izq': ['Deltoides Anterior', 'Deltoides Posterior', 'Supraespinoso'],
    'deltoides_lat_der': ['Deltoides Anterior', 'Deltoides Posterior', 'Supraespinoso'],
    'deltoides_post_izq': ['Deltoides Anterior', 'Deltoides Lateral', 'Infraespinoso'],
    'deltoides_post_der': ['Deltoides Anterior', 'Deltoides Lateral', 'Infraespinoso'],
    'pectoral_sup_izq': ['Pectoral Inferior', 'Deltoides Anterior', 'Serrato Anterior'],
    'pectoral_sup_der': ['Pectoral Inferior', 'Deltoides Anterior', 'Serrato Anterior'],
    'pectoral_inf_izq': ['Pectoral Superior', 'Deltoides Anterior', 'Serrato Anterior'],
    'pectoral_inf_der': ['Pectoral Superior', 'Deltoides Anterior', 'Serrato Anterior'],
    'dorsal_izq': ['Trapecio Medio', 'Trapecio Inferior', 'Romboides', 'Redondo Mayor'],
    'dorsal_der': ['Trapecio Medio', 'Trapecio Inferior', 'Romboides', 'Redondo Mayor'],
    'trapecio_sup_izq': ['Trapecio Medio', 'Trapecio Inferior', 'Elevador de la Escápula'],
    'trapecio_sup_der': ['Trapecio Medio', 'Trapecio Inferior', 'Elevador de la Escápula'],
    'trapecio_med_izq': ['Trapecio Superior', 'Trapecio Inferior', 'Romboides'],
    'trapecio_med_der': ['Trapecio Superior', 'Trapecio Inferior', 'Romboides'],
    'trapecio_inf_izq': ['Trapecio Superior', 'Trapecio Medio', 'Serrato Anterior'],
    'trapecio_inf_der': ['Trapecio Superior', 'Trapecio Medio', 'Serrato Anterior'],
    'infraespinoso_izq': ['Supraespinoso', 'Subescapular', 'Redondo Menor'],
    'infraespinoso_der': ['Supraespinoso', 'Subescapular', 'Redondo Menor'],
    'supraespinoso_izq': ['Infraespinoso', 'Subescapular', 'Deltoides Lateral'],
    'supraespinoso_der': ['Infraespinoso', 'Subescapular', 'Deltoides Lateral'],
    'subescapular_izq': ['Supraespinoso', 'Infraespinoso', 'Redondo Mayor'],
    'subescapular_der': ['Supraespinoso', 'Infraespinoso', 'Redondo Mayor'],
    'redondo_mayor_izq': ['Redondo Menor', 'Infraespinoso', 'Dorsal Ancho'],
    'redondo_mayor_der': ['Redondo Menor', 'Infraespinoso', 'Dorsal Ancho'],
    'romboides_izq': ['Trapecio Medio', 'Trapecio Inferior', 'Dorsal Ancho', 'Elevador de la Escápula'],
    'romboides_der': ['Trapecio Medio', 'Trapecio Inferior', 'Dorsal Ancho', 'Elevador de la Escápula'],
    'abdomen_1_izq': ['Oblicuo Externo', 'Oblicuo Interno', 'Transverso del Abdomen'],
    'abdomen_1_der': ['Oblicuo Externo', 'Oblicuo Interno', 'Transverso del Abdomen'],
    'oblicuo_ext_izq': ['Oblicuo Interno', 'Recto Abdominal', 'Intercostales'],
    'oblicuo_ext_der': ['Oblicuo Interno', 'Recto Abdominal', 'Intercostales'],
    'oblicuo_int_izq': ['Oblicuo Externo', 'Recto Abdominal', 'Transverso del Abdomen'],
    'oblicuo_int_der': ['Oblicuo Externo', 'Recto Abdominal', 'Transverso del Abdomen'],
    'gastrocnemio_izq': ['Sóleo', 'Tibial Posterior', 'Peroneos'],
    'gastrocnemio_der': ['Sóleo', 'Tibial Posterior', 'Peroneos'],
    'soleo_izq': ['Gastrocnemio', 'Tibial Posterior', 'Peroneos'],
    'soleo_der': ['Gastrocnemio', 'Tibial Posterior', 'Peroneos'],
    'psoas_iliaco_izq': ['Cuadrado Lumbar', 'Recto Abdominal', 'Glúteo Mayor'],
    'psoas_iliaco_der': ['Cuadrado Lumbar', 'Recto Abdominal', 'Glúteo Mayor'],
    'cuadrado_lumbar_izq': ['Psoas Ilíaco', 'Iliocostal', 'Oblicuo Interno'],
    'cuadrado_lumbar_der': ['Psoas Ilíaco', 'Iliocostal', 'Oblicuo Interno'],
    'sartorio_izq': ['Recto Femoral', 'Grácil', 'Aductor Largo'],
    'sartorio_der': ['Recto Femoral', 'Grácil', 'Aductor Largo'],
    'tfl_izq': ['Glúteo Medio', 'Glúteo Menor', 'Sartorio'],
    'tfl_der': ['Glúteo Medio', 'Glúteo Menor', 'Sartorio'],
    'piriforme_izq': ['Glúteo Mayor', 'Glúteo Medio', 'Gémino Superior'],
    'piriforme_der': ['Glúteo Mayor', 'Glúteo Medio', 'Gémino Superior'],
    'aductor_largo_izq': ['Aductor Mayor', 'Grácil', 'Pectíneo'],
    'aductor_largo_der': ['Aductor Mayor', 'Grácil', 'Pectíneo'],
    'aductor_mayor_izq': ['Aductor Largo', 'Grácil', 'Isquiotibiales'],
    'aductor_mayor_der': ['Aductor Largo', 'Grácil', 'Isquiotibiales'],
    'gracil_izq': ['Aductor Largo', 'Aductor Mayor', 'Sartorio'],
    'gracil_der': ['Aductor Largo', 'Aductor Mayor', 'Sartorio'],
    'braquial_izq': ['Bíceps Braquial', 'Braquiorradial', 'Coracobraquial'],
    'braquial_der': ['Bíceps Braquial', 'Braquiorradial', 'Coracobraquial'],
    'braquiorradial_izq': ['Braquial', 'Flexores del Antebrazo', 'Extensores del Antebrazo'],
    'braquiorradial_der': ['Braquial', 'Flexores del Antebrazo', 'Extensores del Antebrazo']
};

function esProfundo(id) { return PROFUNDOS.includes(id); }
function esArticulacion(id) { return ARTICULACIONES.includes(id); }
function esEstructura(id) { return ESTRUCTURAS.includes(id); }
function esMusculo(id) { return !esArticulacion(id) && !esEstructura(id); }

const GRUPOS_MUSCULARES = {
    hombro: ['deltoides', 'supraespinoso', 'infraespinoso', 'subescapular', 'redondo_menor'],
    pecho: ['pectoral'],
    espalda: ['dorsal', 'trapecio_med', 'trapecio_inf', 'romboides', 'erector', 'iliocostal', 'longisimo', 'espinoso', 'redondo_mayor'],
    biceps: ['biceps', 'braquial', 'coracobraquial'],
    triceps: ['triceps', 'anconeo'],
    antebrazo: ['antebrazo', 'braquiorradial'],
    cuello: ['esternocleidomastoideo', 'largo_cuello', 'largo_cabeza', 'recto_ant', 'esplenio', 'oblicuo_sup_cabeza', 'oblicuo_inf_cabeza', 'trapecio_sup', 'elevador'],
    core: ['abdomen', 'oblicuo', 'transverso'],
    gluteo: ['gluteo', 'piriforme', 'gemino', 'cuadrado_femoral'],
    cuadriceps: ['cuadriceps', 'vastolateral', 'vastomedial', 'vastointermedio'],
    isquio: ['biceps_femoral', 'semitendinoso', 'semimembranoso'],
    pantorrilla: ['gastrocnemio', 'soleo', 'tibial', 'peroneo'],
    aductor: ['aductor', 'gracil', 'pectineo', 'sartorio']
};

function obtenerGrupoMuscular(ejercicio) {
    const primarios = (ejercicio.primary || []).flatMap(g => g.meshes);
    for (const grupo in GRUPOS_MUSCULARES) {
        if (primarios.some(m => GRUPOS_MUSCULARES[grupo].some(p => m.includes(p)))) return grupo;
    }
    return 'otros';
}

let filtroEquipo = 'todos';
let filtroGrupo = 'todos';
let musculoSeleccionado = null;

const container = document.getElementById('canvas-container');
const scene = new THREE.Scene();
scene.background = new THREE.Color(0x0a0a0a);
scene.fog = new THREE.Fog(0x0a0a0a, 10, 20);

const camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 0.1, 1000);
camera.position.set(0, 1.5, 6.5);

const renderer = new THREE.WebGLRenderer({ antialias: true });
renderer.setSize(window.innerWidth, window.innerHeight);
renderer.shadowMap.enabled = true;
renderer.shadowMap.type = THREE.PCFSoftShadowMap;
container.appendChild(renderer.domElement);

const controls = new OrbitControls(camera, renderer.domElement);
controls.target.set(0, 1.2, 0);
controls.enableDamping = true;
controls.dampingFactor = 0.05;
controls.update();

const ambientLight = new THREE.AmbientLight(0xffffff, 0.4);
scene.add(ambientLight);
const dirLight = new THREE.DirectionalLight(0xffffff, 1.5);
dirLight.position.set(5, 10, 5);
dirLight.castShadow = true;
dirLight.shadow.mapSize.width = 2048;
dirLight.shadow.mapSize.height = 2048;
dirLight.shadow.camera.near = 0.5;
dirLight.shadow.camera.far = 25;
dirLight.shadow.camera.left = -6;
dirLight.shadow.camera.right = 6;
dirLight.shadow.camera.top = 6;
dirLight.shadow.camera.bottom = -6;
scene.add(dirLight);
const fillLight = new THREE.DirectionalLight(0xaaccff, 0.8);
fillLight.position.set(-5, 5, 2);
scene.add(fillLight);
const rimLight = new THREE.DirectionalLight(0xffffff, 1.0);
rimLight.position.set(-2, 3, -5);
scene.add(rimLight);

const floor = new THREE.Mesh(new THREE.PlaneGeometry(20, 20), new THREE.MeshStandardMaterial({ color: 0x151515, roughness: 0.8, metalness: 0.2 }));
floor.rotation.x = -Math.PI / 2;
floor.position.y = -1.5;
floor.receiveShadow = true;
scene.add(floor);
const gridHelper = new THREE.GridHelper(20, 20, 0x333333, 0x222222);
gridHelper.position.y = -1.49;
scene.add(gridHelper);

const materialMusculoBase = { color: 0xaa3333, roughness: 0.6, metalness: 0.1 };
const materialProfundoBase = { color: 0x772222, roughness: 0.6, metalness: 0.1 };
const materialHuesoBase = { color: 0xd0d8e0, roughness: 0.5, metalness: 0.1 };
const materialPrimaryBase = { color: 0xff0000, emissive: 0xaa0000, emissiveIntensity: 1.5, roughness: 0.3 };
const materialSecondaryBase = { color: 0xff8800, emissive: 0x884400, emissiveIntensity: 1.0, roughness: 0.3 };
const materialStabilizerBase = { color: 0xffdd00, emissive: 0x887700, emissiveIntensity: 0.8, roughness: 0.3 };
const materialJointBase = { color: 0x00ccff, emissive: 0x006688, emissiveIntensity: 1.0, roughness: 0.3 };
const materialSeleccionBase = { color: 0x1a3d8f, emissive: 0x0a1a4a, emissiveIntensity: 1.2, roughness: 0.4 };

function crearMaterial(baseMat) {
    return new THREE.MeshStandardMaterial(baseMat);
}

function reemplazarMaterial(mesh, nuevoMat) {
    const anterior = mesh.material;
    mesh.material = nuevoMat;
    if (anterior && anterior !== mesh.userData.materialAntes) {
        anterior.dispose();
    }
}

const materialMusculo = new THREE.MeshStandardMaterial(materialMusculoBase);
const materialProfundo = new THREE.MeshStandardMaterial(materialProfundoBase);
const materialHueso = new THREE.MeshStandardMaterial(materialHuesoBase);

const materialOutline = new THREE.LineBasicMaterial({ color: 0x000000 });

const partes = {};
function crearParte(geometria, posicion, nombre, rotacion = {x:0, y:0, z:0}, material = null, escala = {x:1, y:1, z:1}) {
    if (!material) material = esProfundo(nombre) ? materialProfundo : ((esArticulacion(nombre) || esEstructura(nombre)) ? materialHueso : materialMusculo);
    const matClonado = material.clone();
    const mesh = new THREE.Mesh(geometria, matClonado);
    mesh.position.set(posicion.x, posicion.y, posicion.z);
    mesh.rotation.set(rotacion.x, rotacion.y, rotacion.z);
    mesh.scale.set(escala.x, escala.y, escala.z);
    mesh.castShadow = true;
    mesh.receiveShadow = true;
    mesh.name = nombre;

    const edges = new THREE.EdgesGeometry(geometria, 1);
    const outline = new THREE.LineSegments(edges, materialOutline);
    outline.userData.esOutline = true;
    mesh.add(outline);

    scene.add(mesh);
    partes[nombre] = mesh;
    return mesh;
}

crearParte(new THREE.BoxGeometry(0.45, 0.55, 0.45), {x:0, y:3.0, z:0}, 'cabeza', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.BoxGeometry(0.2, 0.2, 0.2), {x:0, y:2.65, z:0}, 'cuello', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.BoxGeometry(0.08, 0.25, 0.08), {x:-0.12, y:2.6, z:0.1}, 'esternocleidomastoideo_izq', {z:0.2});
crearParte(new THREE.BoxGeometry(0.08, 0.25, 0.08), {x:0.12, y:2.6, z:0.1}, 'esternocleidomastoideo_der', {z:-0.2});
crearParte(new THREE.BoxGeometry(0.05, 0.18, 0.04), {x:-0.04, y:2.58, z:0.02}, 'largo_cuello_izq');
crearParte(new THREE.BoxGeometry(0.05, 0.18, 0.04), {x:0.04, y:2.58, z:0.02}, 'largo_cuello_der');
crearParte(new THREE.BoxGeometry(0.04, 0.12, 0.04), {x:-0.04, y:2.72, z:0.03}, 'largo_cabeza_izq');
crearParte(new THREE.BoxGeometry(0.04, 0.12, 0.04), {x:0.04, y:2.72, z:0.03}, 'largo_cabeza_der');
crearParte(new THREE.BoxGeometry(0.04, 0.06, 0.04), {x:-0.03, y:2.80, z:0.04}, 'recto_ant_cabeza_izq');
crearParte(new THREE.BoxGeometry(0.04, 0.06, 0.04), {x:0.03, y:2.80, z:0.04}, 'recto_ant_cabeza_der');
crearParte(new THREE.BoxGeometry(0.1, 0.1, 0.1), {x:-0.18, y:2.95, z:0.15}, 'masetero_izq');
crearParte(new THREE.BoxGeometry(0.1, 0.1, 0.1), {x:0.18, y:2.95, z:0.15}, 'masetero_der');
crearParte(new THREE.BoxGeometry(0.2, 0.15, 0.1), {x:0, y:3.1, z:-0.2}, 'occipital');
crearParte(new THREE.BoxGeometry(0.06, 0.15, 0.06), {x:-0.08, y:2.68, z:-0.08}, 'esplenio_izq');
crearParte(new THREE.BoxGeometry(0.06, 0.15, 0.06), {x:0.08, y:2.68, z:-0.08}, 'esplenio_der');
crearParte(new THREE.BoxGeometry(0.04, 0.05, 0.04), {x:-0.05, y:2.88, z:-0.04}, 'oblicuo_sup_cabeza_izq');
crearParte(new THREE.BoxGeometry(0.04, 0.05, 0.04), {x:0.05, y:2.88, z:-0.04}, 'oblicuo_sup_cabeza_der');
crearParte(new THREE.BoxGeometry(0.04, 0.05, 0.04), {x:-0.05, y:2.85, z:-0.06}, 'oblicuo_inf_cabeza_izq');
crearParte(new THREE.BoxGeometry(0.04, 0.05, 0.04), {x:0.05, y:2.85, z:-0.06}, 'oblicuo_inf_cabeza_der');
crearParte(new THREE.BoxGeometry(0.1, 0.18, 0.08), {x:-0.32, y:2.62, z:-0.02}, 'elevador_escapula_izq', {z:0.2});
crearParte(new THREE.BoxGeometry(0.1, 0.18, 0.08), {x:0.32, y:2.62, z:-0.02}, 'elevador_escapula_der', {z:-0.2});

crearParte(new THREE.BoxGeometry(0.45, 0.25, 0.4), {x:-0.28, y:2.3, z:0.15}, 'pectoral_sup_izq');
crearParte(new THREE.BoxGeometry(0.45, 0.25, 0.4), {x:0.28, y:2.3, z:0.15}, 'pectoral_sup_der');
crearParte(new THREE.BoxGeometry(0.45, 0.25, 0.4), {x:-0.28, y:2.05, z:0.15}, 'pectoral_inf_izq');
crearParte(new THREE.BoxGeometry(0.45, 0.25, 0.4), {x:0.28, y:2.05, z:0.15}, 'pectoral_inf_der');
crearParte(new THREE.BoxGeometry(0.2, 0.15, 0.15), {x:-0.2, y:2.05, z:0.05}, 'pectoral_menor_izq');
crearParte(new THREE.BoxGeometry(0.2, 0.15, 0.15), {x:0.2, y:2.05, z:0.05}, 'pectoral_menor_der');

for(let i=0; i<4; i++) {
    crearParte(new THREE.BoxGeometry(0.05, 0.05, 0.15), {x:-0.5, y:2.05 - i*0.13, z:0.05}, `intercostal_izq_${i}`);
    crearParte(new THREE.BoxGeometry(0.05, 0.05, 0.15), {x:0.5, y:2.05 - i*0.13, z:0.05}, `intercostal_der_${i}`);
}

for(let i=0; i<3; i++) {
    crearParte(new THREE.BoxGeometry(0.08, 0.08, 0.1), {x:-0.52, y:2.15 - i*0.1, z:0.1}, `serrato_izq_${i}`, {z:0.3});
    crearParte(new THREE.BoxGeometry(0.08, 0.08, 0.1), {x:0.52, y:2.15 - i*0.1, z:0.1}, `serrato_der_${i}`, {z:-0.3});
}

crearParte(new THREE.BoxGeometry(0.15, 0.12, 0.1), {x:-0.1, y:1.75, z:0.2}, 'abdomen_1_izq');
crearParte(new THREE.BoxGeometry(0.15, 0.12, 0.1), {x:0.1, y:1.75, z:0.2}, 'abdomen_1_der');
crearParte(new THREE.BoxGeometry(0.15, 0.12, 0.1), {x:-0.1, y:1.55, z:0.2}, 'abdomen_2_izq');
crearParte(new THREE.BoxGeometry(0.15, 0.12, 0.1), {x:0.1, y:1.55, z:0.2}, 'abdomen_2_der');
crearParte(new THREE.BoxGeometry(0.15, 0.12, 0.1), {x:-0.1, y:1.35, z:0.2}, 'abdomen_3_izq');
crearParte(new THREE.BoxGeometry(0.15, 0.12, 0.1), {x:0.1, y:1.35, z:0.2}, 'abdomen_3_der');
crearParte(new THREE.BoxGeometry(0.3, 0.5, 0.05), {x:0, y:1.55, z:0.02}, 'transverso_abdominal');
crearParte(new THREE.BoxGeometry(0.12, 0.5, 0.25), {x:-0.42, y:1.55, z:0.05}, 'oblicuo_ext_izq');
crearParte(new THREE.BoxGeometry(0.12, 0.5, 0.25), {x:0.42, y:1.55, z:0.05}, 'oblicuo_ext_der');
crearParte(new THREE.BoxGeometry(0.1, 0.4, 0.2), {x:-0.35, y:1.55, z:0.1}, 'oblicuo_int_izq');
crearParte(new THREE.BoxGeometry(0.1, 0.4, 0.2), {x:0.35, y:1.55, z:0.1}, 'oblicuo_int_der');
crearParte(new THREE.BoxGeometry(0.08, 0.4, 0.08), {x:-0.08, y:1.3, z:-0.05}, 'psoas_iliaco_izq');
crearParte(new THREE.BoxGeometry(0.08, 0.4, 0.08), {x:0.08, y:1.3, z:-0.05}, 'psoas_iliaco_der');

crearParte(new THREE.BoxGeometry(0.35, 0.5, 0.2), {x:-0.35, y:2.1, z:-0.2}, 'dorsal_izq', {z:-0.2});
crearParte(new THREE.BoxGeometry(0.35, 0.5, 0.2), {x:0.35, y:2.1, z:-0.2}, 'dorsal_der', {z:0.2});
crearParte(new THREE.BoxGeometry(0.04, 0.75, 0.1), {x:-0.19, y:1.85, z:-0.2}, 'iliocostal_izq');
crearParte(new THREE.BoxGeometry(0.04, 0.75, 0.1), {x:0.19, y:1.85, z:-0.2}, 'iliocostal_der');
crearParte(new THREE.BoxGeometry(0.04, 0.75, 0.1), {x:-0.1, y:1.85, z:-0.2}, 'longisimo_izq');
crearParte(new THREE.BoxGeometry(0.04, 0.75, 0.1), {x:0.1, y:1.85, z:-0.2}, 'longisimo_der');
crearParte(new THREE.BoxGeometry(0.04, 0.75, 0.1), {x:-0.02, y:1.85, z:-0.2}, 'espinoso_izq');
crearParte(new THREE.BoxGeometry(0.04, 0.75, 0.1), {x:0.02, y:1.85, z:-0.2}, 'espinoso_der');
crearParte(new THREE.BoxGeometry(0.1, 0.75, 0.12), {x:0, y:1.85, z:-0.25}, 'erector_espinal_izq', {x:0, y:0, z:0}, null, {x:0.01, y:0.01, z:0.01});
crearParte(new THREE.BoxGeometry(0.1, 0.75, 0.12), {x:0, y:1.85, z:-0.25}, 'erector_espinal_der', {x:0, y:0, z:0}, null, {x:0.01, y:0.01, z:0.01});
crearParte(new THREE.BoxGeometry(0.15, 0.15, 0.15), {x:-0.4, y:2.25, z:-0.15}, 'infraespinoso_izq');
crearParte(new THREE.BoxGeometry(0.15, 0.15, 0.15), {x:0.4, y:2.25, z:-0.15}, 'infraespinoso_der');
crearParte(new THREE.BoxGeometry(0.1, 0.1, 0.1), {x:-0.5, y:2.1, z:-0.1}, 'redondo_mayor_izq');
crearParte(new THREE.BoxGeometry(0.1, 0.1, 0.1), {x:0.5, y:2.1, z:-0.1}, 'redondo_mayor_der');
crearParte(new THREE.BoxGeometry(0.08, 0.08, 0.08), {x:-0.45, y:2.25, z:-0.15}, 'redondo_menor_izq');
crearParte(new THREE.BoxGeometry(0.08, 0.08, 0.08), {x:0.45, y:2.25, z:-0.15}, 'redondo_menor_der');
crearParte(new THREE.BoxGeometry(0.2, 0.1, 0.2), {x:-0.25, y:2.55, z:-0.1}, 'trapecio_sup_izq', {z:0.3});
crearParte(new THREE.BoxGeometry(0.2, 0.1, 0.2), {x:0.25, y:2.55, z:-0.1}, 'trapecio_sup_der', {z:-0.3});
crearParte(new THREE.BoxGeometry(0.25, 0.15, 0.2), {x:-0.35, y:2.35, z:-0.15}, 'trapecio_med_izq');
crearParte(new THREE.BoxGeometry(0.25, 0.15, 0.2), {x:0.35, y:2.35, z:-0.15}, 'trapecio_med_der');
crearParte(new THREE.BoxGeometry(0.2, 0.15, 0.2), {x:-0.2, y:2.05, z:-0.2}, 'trapecio_inf_izq');
crearParte(new THREE.BoxGeometry(0.2, 0.15, 0.2), {x:0.2, y:2.05, z:-0.2}, 'trapecio_inf_der');
crearParte(new THREE.BoxGeometry(0.15, 0.15, 0.1), {x:-0.3, y:2.4, z:-0.15}, 'romboides_izq');
crearParte(new THREE.BoxGeometry(0.15, 0.15, 0.1), {x:0.3, y:2.4, z:-0.15}, 'romboides_der');
crearParte(new THREE.BoxGeometry(0.15, 0.15, 0.1), {x:-0.35, y:2.3, z:-0.1}, 'subescapular_izq');
crearParte(new THREE.BoxGeometry(0.15, 0.15, 0.1), {x:0.35, y:2.3, z:-0.1}, 'subescapular_der');
crearParte(new THREE.BoxGeometry(0.1, 0.1, 0.1), {x:-0.5, y:2.45, z:-0.05}, 'supraespinoso_izq');
crearParte(new THREE.BoxGeometry(0.1, 0.1, 0.1), {x:0.5, y:2.45, z:-0.05}, 'supraespinoso_der');
crearParte(new THREE.BoxGeometry(0.08, 0.08, 0.06), {x:-0.35, y:2.3, z:-0.22}, 'serrato_post_sup_izq');
crearParte(new THREE.BoxGeometry(0.08, 0.08, 0.06), {x:0.35, y:2.3, z:-0.22}, 'serrato_post_sup_der');
crearParte(new THREE.BoxGeometry(0.15, 0.1, 0.1), {x:-0.15, y:1.5, z:-0.22}, 'cuadrado_lumbar_izq');
crearParte(new THREE.BoxGeometry(0.15, 0.1, 0.1), {x:0.15, y:1.5, z:-0.22}, 'cuadrado_lumbar_der');
crearParte(new THREE.BoxGeometry(0.1, 0.08, 0.06), {x:-0.35, y:1.75, z:-0.22}, 'serrato_post_inf_izq');
crearParte(new THREE.BoxGeometry(0.1, 0.08, 0.06), {x:0.35, y:1.75, z:-0.22}, 'serrato_post_inf_der');

crearParte(new THREE.BoxGeometry(0.22, 0.18, 0.22), {x:-0.68, y:2.4, z:0.1}, 'deltoides_ant_izq');
crearParte(new THREE.BoxGeometry(0.22, 0.18, 0.22), {x:0.68, y:2.4, z:0.1}, 'deltoides_ant_der');
crearParte(new THREE.BoxGeometry(0.22, 0.18, 0.22), {x:-0.8, y:2.4, z:0.05}, 'deltoides_lat_izq');
crearParte(new THREE.BoxGeometry(0.22, 0.18, 0.22), {x:0.8, y:2.4, z:0.05}, 'deltoides_lat_der');
crearParte(new THREE.BoxGeometry(0.22, 0.18, 0.22), {x:-0.68, y:2.4, z:-0.12}, 'deltoides_post_izq');
crearParte(new THREE.BoxGeometry(0.22, 0.18, 0.22), {x:0.68, y:2.4, z:-0.12}, 'deltoides_post_der');

crearParte(new THREE.BoxGeometry(0.08, 0.2, 0.1), {x:-0.63, y:2.18, z:0.08}, 'coracobraquial_izq', {z:0.15});
crearParte(new THREE.BoxGeometry(0.08, 0.2, 0.1), {x:0.63, y:2.18, z:0.08}, 'coracobraquial_der', {z:-0.15});

crearParte(new THREE.BoxGeometry(0.13, 0.25, 0.15), {x:-0.72, y:1.95, z:0.05}, 'biceps_corto_izq');
crearParte(new THREE.BoxGeometry(0.13, 0.25, 0.15), {x:0.72, y:1.95, z:0.05}, 'biceps_corto_der');
crearParte(new THREE.BoxGeometry(0.13, 0.25, 0.15), {x:-0.83, y:1.95, z:0.05}, 'biceps_largo_izq');
crearParte(new THREE.BoxGeometry(0.13, 0.25, 0.15), {x:0.83, y:1.95, z:0.05}, 'biceps_largo_der');
crearParte(new THREE.BoxGeometry(0.1, 0.15, 0.1), {x:-0.78, y:1.75, z:0.05}, 'braquial_izq');
crearParte(new THREE.BoxGeometry(0.1, 0.15, 0.1), {x:0.78, y:1.75, z:0.05}, 'braquial_der');
crearParte(new THREE.BoxGeometry(0.13, 0.3, 0.13), {x:-0.78, y:1.95, z:-0.1}, 'triceps_largo_izq');
crearParte(new THREE.BoxGeometry(0.13, 0.3, 0.13), {x:0.78, y:1.95, z:-0.1}, 'triceps_largo_der');
crearParte(new THREE.BoxGeometry(0.1, 0.2, 0.1), {x:-0.88, y:1.9, z:-0.05}, 'triceps_lat_izq');
crearParte(new THREE.BoxGeometry(0.1, 0.2, 0.1), {x:0.88, y:1.9, z:-0.05}, 'triceps_lat_der');
crearParte(new THREE.BoxGeometry(0.08, 0.15, 0.1), {x:-0.68, y:1.9, z:-0.1}, 'triceps_med_izq');
crearParte(new THREE.BoxGeometry(0.08, 0.15, 0.1), {x:0.68, y:1.9, z:-0.1}, 'triceps_med_der');
crearParte(new THREE.BoxGeometry(0.07, 0.08, 0.07), {x:-0.78, y:1.68, z:-0.1}, 'anconeo_izq');
crearParte(new THREE.BoxGeometry(0.07, 0.08, 0.07), {x:0.78, y:1.68, z:-0.1}, 'anconeo_der');
crearParte(new THREE.BoxGeometry(0.1, 0.3, 0.12), {x:-0.78, y:1.45, z:0.05}, 'antebrazo_flex_izq');
crearParte(new THREE.BoxGeometry(0.1, 0.3, 0.12), {x:0.78, y:1.45, z:0.05}, 'antebrazo_flex_der');
crearParte(new THREE.BoxGeometry(0.08, 0.3, 0.1), {x:-0.78, y:1.45, z:-0.05}, 'antebrazo_ext_izq');
crearParte(new THREE.BoxGeometry(0.08, 0.3, 0.1), {x:0.78, y:1.45, z:-0.05}, 'antebrazo_ext_der');
crearParte(new THREE.BoxGeometry(0.06, 0.25, 0.08), {x:-0.73, y:1.55, z:0.1}, 'braquiorradial_izq');
crearParte(new THREE.BoxGeometry(0.06, 0.25, 0.08), {x:0.73, y:1.55, z:0.1}, 'braquiorradial_der');

crearParte(new THREE.BoxGeometry(0.18, 0.22, 0.09), {x:-0.78, y:1.04, z:0.05}, 'mano_izq', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.BoxGeometry(0.18, 0.22, 0.09), {x:0.78, y:1.04, z:0.05}, 'mano_der', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.BoxGeometry(0.17, 0.20, 0.10), {x:-0.78, y:1.05, z:0.05}, 'mano_izq_palma', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.BoxGeometry(0.17, 0.20, 0.10), {x:0.78, y:1.05, z:0.05}, 'mano_der_palma', {x:0, y:0, z:0}, materialHueso);

const dedoOffsets = [-0.055, -0.018, 0.018, 0.055];
const dedoAlturas = [0.14, 0.16, 0.15, 0.12];
const dedoAncho = 0.032;
const dedoLargo = 0.14;
dedoOffsets.forEach((offset, i) => {
    crearParte(new THREE.BoxGeometry(dedoAncho, dedoLargo, 0.08), {x:-0.78 + offset, y:1.04 - dedoAlturas[i]*0.5 - dedoLargo*0.45, z:0.05}, `mano_izq_dedo_${i}`, {x:0, y:0, z:0}, materialHueso);
    crearParte(new THREE.BoxGeometry(dedoAncho, dedoLargo, 0.08), {x:0.78 + offset, y:1.04 - dedoAlturas[i]*0.5 - dedoLargo*0.45, z:0.05}, `mano_der_dedo_${i}`, {x:0, y:0, z:0}, materialHueso);
});
crearParte(new THREE.BoxGeometry(0.05, 0.10, 0.08), {x:-0.70, y:0.98, z:0.05}, 'mano_izq_pulgar', {x:0, y:0, z:0.5}, materialHueso);
crearParte(new THREE.BoxGeometry(0.05, 0.10, 0.08), {x:0.70, y:0.98, z:0.05}, 'mano_der_pulgar', {x:0, y:0, z:-0.5}, materialHueso);

crearParte(new THREE.BoxGeometry(0.35, 0.25, 0.3), {x:-0.25, y:1.0, z:-0.15}, 'gluteo_mayor_izq');
crearParte(new THREE.BoxGeometry(0.35, 0.25, 0.3), {x:0.25, y:1.0, z:-0.15}, 'gluteo_mayor_der');
crearParte(new THREE.BoxGeometry(0.2, 0.15, 0.15), {x:-0.45, y:1.05, z:-0.1}, 'gluteo_med_izq');
crearParte(new THREE.BoxGeometry(0.2, 0.15, 0.15), {x:0.45, y:1.05, z:-0.1}, 'gluteo_med_der');
crearParte(new THREE.BoxGeometry(0.15, 0.1, 0.1), {x:-0.3, y:1.1, z:-0.2}, 'gluteo_menor_izq');
crearParte(new THREE.BoxGeometry(0.15, 0.1, 0.1), {x:0.3, y:1.1, z:-0.2}, 'gluteo_menor_der');
crearParte(new THREE.BoxGeometry(0.1, 0.15, 0.1), {x:-0.3, y:1.0, z:-0.3}, 'piriforme_izq');
crearParte(new THREE.BoxGeometry(0.1, 0.15, 0.1), {x:0.3, y:1.0, z:-0.3}, 'piriforme_der');
crearParte(new THREE.BoxGeometry(0.05, 0.05, 0.05), {x:-0.3, y:1.02, z:-0.35}, 'gemino_sup_izq');
crearParte(new THREE.BoxGeometry(0.05, 0.05, 0.05), {x:0.3, y:1.02, z:-0.35}, 'gemino_sup_der');
crearParte(new THREE.BoxGeometry(0.05, 0.05, 0.05), {x:-0.3, y:0.96, z:-0.35}, 'gemino_inf_izq');
crearParte(new THREE.BoxGeometry(0.05, 0.05, 0.05), {x:0.3, y:0.96, z:-0.35}, 'gemino_inf_der');
crearParte(new THREE.BoxGeometry(0.06, 0.08, 0.06), {x:-0.35, y:0.9, z:-0.32}, 'cuadrado_femoral_izq');
crearParte(new THREE.BoxGeometry(0.06, 0.08, 0.06), {x:0.35, y:0.9, z:-0.32}, 'cuadrado_femoral_der');

crearParte(new THREE.BoxGeometry(0.15, 0.5, 0.15), {x:-0.25, y:0.5, z:0.15}, 'cuadriceps_recto_izq');
crearParte(new THREE.BoxGeometry(0.15, 0.5, 0.15), {x:0.25, y:0.5, z:0.15}, 'cuadriceps_recto_der');
crearParte(new THREE.BoxGeometry(0.15, 0.5, 0.15), {x:-0.45, y:0.5, z:0.05}, 'vastolateral_izq');
crearParte(new THREE.BoxGeometry(0.15, 0.5, 0.15), {x:0.45, y:0.5, z:0.05}, 'vastolateral_der');
crearParte(new THREE.BoxGeometry(0.1, 0.5, 0.1), {x:-0.1, y:0.5, z:0.1}, 'vastomedial_izq');
crearParte(new THREE.BoxGeometry(0.1, 0.5, 0.1), {x:0.1, y:0.5, z:0.1}, 'vastomedial_der');
crearParte(new THREE.BoxGeometry(0.08, 0.4, 0.1), {x:-0.25, y:0.5, z:0.05}, 'vastointermedio_izq');
crearParte(new THREE.BoxGeometry(0.08, 0.4, 0.1), {x:0.25, y:0.5, z:0.05}, 'vastointermedio_der');

crearParte(new THREE.BoxGeometry(0.15, 0.5, 0.15), {x:-0.25, y:0.5, z:-0.15}, 'biceps_femoral_izq');
crearParte(new THREE.BoxGeometry(0.15, 0.5, 0.15), {x:0.25, y:0.5, z:-0.15}, 'biceps_femoral_der');
crearParte(new THREE.BoxGeometry(0.12, 0.4, 0.12), {x:-0.35, y:0.5, z:-0.1}, 'semitendinoso_izq');
crearParte(new THREE.BoxGeometry(0.12, 0.4, 0.12), {x:0.35, y:0.5, z:-0.1}, 'semitendinoso_der');
crearParte(new THREE.BoxGeometry(0.12, 0.4, 0.12), {x:-0.15, y:0.5, z:-0.1}, 'semimembranoso_izq');
crearParte(new THREE.BoxGeometry(0.12, 0.4, 0.12), {x:0.15, y:0.5, z:-0.1}, 'semimembranoso_der');

crearParte(new THREE.BoxGeometry(0.08, 0.4, 0.1), {x:-0.05, y:0.5, z:0.0}, 'aductor_largo_izq');
crearParte(new THREE.BoxGeometry(0.08, 0.4, 0.1), {x:0.05, y:0.5, z:0.0}, 'aductor_largo_der');
crearParte(new THREE.BoxGeometry(0.1, 0.4, 0.1), {x:-0.12, y:0.45, z:0.05}, 'aductor_mayor_izq');
crearParte(new THREE.BoxGeometry(0.1, 0.4, 0.1), {x:0.12, y:0.45, z:0.05}, 'aductor_mayor_der');
crearParte(new THREE.BoxGeometry(0.04, 0.15, 0.05), {x:-0.08, y:0.6, z:0.03}, 'aductor_corto_izq');
crearParte(new THREE.BoxGeometry(0.04, 0.15, 0.05), {x:0.08, y:0.6, z:0.03}, 'aductor_corto_der');
crearParte(new THREE.BoxGeometry(0.05, 0.1, 0.06), {x:-0.02, y:0.7, z:0.08}, 'pectineo_izq');
crearParte(new THREE.BoxGeometry(0.05, 0.1, 0.06), {x:0.02, y:0.7, z:0.08}, 'pectineo_der');
crearParte(new THREE.BoxGeometry(0.06, 0.45, 0.06), {x:-0.2, y:0.5, z:0.05}, 'gracil_izq');
crearParte(new THREE.BoxGeometry(0.06, 0.45, 0.06), {x:0.2, y:0.5, z:0.05}, 'gracil_der');
crearParte(new THREE.BoxGeometry(0.05, 0.6, 0.05), {x:-0.35, y:0.6, z:0.15}, 'sartorio_izq');
crearParte(new THREE.BoxGeometry(0.05, 0.6, 0.05), {x:0.35, y:0.6, z:0.15}, 'sartorio_der');
crearParte(new THREE.BoxGeometry(0.08, 0.25, 0.08), {x:-0.55, y:0.9, z:0.05}, 'tfl_izq');
crearParte(new THREE.BoxGeometry(0.08, 0.25, 0.08), {x:0.55, y:0.9, z:0.05}, 'tfl_der');

crearParte(new THREE.BoxGeometry(0.15, 0.35, 0.15), {x:-0.25, y:-0.35, z:0.05}, 'gastrocnemio_izq');
crearParte(new THREE.BoxGeometry(0.15, 0.35, 0.15), {x:0.25, y:-0.35, z:0.05}, 'gastrocnemio_der');
crearParte(new THREE.BoxGeometry(0.12, 0.25, 0.12), {x:-0.25, y:-0.45, z:-0.05}, 'soleo_izq');
crearParte(new THREE.BoxGeometry(0.12, 0.25, 0.12), {x:0.25, y:-0.45, z:-0.05}, 'soleo_der');
crearParte(new THREE.BoxGeometry(0.08, 0.3, 0.08), {x:-0.25, y:-0.4, z:0.15}, 'tibial_izq');
crearParte(new THREE.BoxGeometry(0.08, 0.3, 0.08), {x:0.25, y:-0.4, z:0.15}, 'tibial_der');
crearParte(new THREE.BoxGeometry(0.06, 0.3, 0.06), {x:-0.25, y:-0.4, z:-0.1}, 'tibial_posterior_izq');
crearParte(new THREE.BoxGeometry(0.06, 0.3, 0.06), {x:0.25, y:-0.4, z:-0.1}, 'tibial_posterior_der');
crearParte(new THREE.BoxGeometry(0.06, 0.25, 0.06), {x:-0.35, y:-0.4, z:0.05}, 'peroneo_izq');
crearParte(new THREE.BoxGeometry(0.06, 0.25, 0.06), {x:0.35, y:-0.4, z:0.05}, 'peroneo_der');
crearParte(new THREE.BoxGeometry(0.05, 0.15, 0.05), {x:-0.25, y:-0.15, z:-0.1}, 'popliteo_izq');
crearParte(new THREE.BoxGeometry(0.05, 0.15, 0.05), {x:0.25, y:-0.15, z:-0.1}, 'popliteo_der');
crearParte(new THREE.BoxGeometry(0.05, 0.2, 0.05), {x:-0.25, y:-0.6, z:0.15}, 'extensor_dedos_izq');
crearParte(new THREE.BoxGeometry(0.05, 0.2, 0.05), {x:0.25, y:-0.6, z:0.15}, 'extensor_dedos_der');

crearParte(new THREE.BoxGeometry(0.18, 0.1, 0.3), {x:-0.25, y:-0.9, z:0.08}, 'pie_izq', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.BoxGeometry(0.18, 0.1, 0.3), {x:0.25, y:-0.9, z:0.08}, 'pie_der', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.BoxGeometry(0.12, 0.05, 0.1), {x:-0.25, y:-0.92, z:0.25}, 'intrinsecos_pie_izq');
crearParte(new THREE.BoxGeometry(0.12, 0.05, 0.1), {x:0.25, y:-0.92, z:0.25}, 'intrinsecos_pie_der');

crearParte(new THREE.SphereGeometry(0.1, 20, 20), {x:-0.78, y:2.18, z:0}, 'hombro_izq', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.SphereGeometry(0.1, 20, 20), {x:0.78, y:2.18, z:0}, 'hombro_der', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.SphereGeometry(0.1, 20, 20), {x:-0.78, y:1.7, z:0}, 'codo_izq', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.SphereGeometry(0.1, 20, 20), {x:0.78, y:1.7, z:0}, 'codo_der', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.SphereGeometry(0.08, 20, 20), {x:-0.78, y:1.2, z:0.05}, 'muneca_izq', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.SphereGeometry(0.08, 20, 20), {x:0.78, y:1.2, z:0.05}, 'muneca_der', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.SphereGeometry(0.17, 20, 20), {x:-0.3, y:0.9, z:0}, 'cadera_izq', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.SphereGeometry(0.17, 20, 20), {x:0.3, y:0.9, z:0}, 'cadera_der', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.SphereGeometry(0.15, 20, 20), {x:-0.25, y:0.1, z:0}, 'rodilla_izq', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.SphereGeometry(0.15, 20, 20), {x:0.25, y:0.1, z:0}, 'rodilla_der', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.SphereGeometry(0.11, 20, 20), {x:-0.25, y:-0.8, z:0}, 'tobillo_izq', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.SphereGeometry(0.11, 20, 20), {x:0.25, y:-0.8, z:0}, 'tobillo_der', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.CylinderGeometry(0.06, 0.06, 0.4, 8), {x:0, y:2.55, z:-0.05}, 'columna_cervical', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.CylinderGeometry(0.07, 0.07, 0.7, 8), {x:0, y:1.95, z:-0.1}, 'columna_toracica', {x:0, y:0, z:0}, materialHueso);
crearParte(new THREE.CylinderGeometry(0.07, 0.07, 0.5, 8), {x:0, y:1.4, z:-0.1}, 'columna_lumbar', {x:0, y:0, z:0}, materialHueso);

function validarDatos() {
    const idsValidos = new Set(Object.keys(partes));
    const errores = [];
    for (const clave in baseDatos) {
        const datos = baseDatos[clave];
        const categorias = ['primary', 'secondary', 'stabilizers', 'joints'];
        for (const cat of categorias) {
            for (const grupo of (datos[cat] || [])) {
                for (const id of grupo.meshes) {
                    if (!idsValidos.has(id)) errores.push(`[${clave}][${cat}] mesh inexistente: ${id}`);
                }
            }
        }
    }
    if (errores.length > 0) {
        console.warn('=== VALIDACIÓN: ' + errores.length + ' errores ===');
        errores.forEach(e => console.warn(e));
    } else {
        console.log('✓ Validación OK');
    }
}
validarDatos();

function validarCoberturaInfo() {
    const faltantesNombre = [];
    const faltantesInfo = [];
    Object.keys(partes).forEach(id => {
        if (!nombresMusculos[id]) faltantesNombre.push(id);
        if (!infoMusculos[id]) faltantesInfo.push(id);
    });
    if (faltantesNombre.length > 0) {
        console.warn(`⚠ ${faltantesNombre.length} meshes sin nombre:`);
        faltantesNombre.forEach(n => console.warn('  - ' + n));
    }
    if (faltantesInfo.length > 0) {
        console.warn(`⚠ ${faltantesInfo.length} meshes sin info:`);
        faltantesInfo.forEach(n => console.warn('  - ' + n));
    }
    if (faltantesNombre.length === 0 && faltantesInfo.length === 0) {
        console.log('✓ Todos los meshes tienen nombre e info');
    }
}
validarCoberturaInfo();

function restaurarSeleccion() {
    if (musculoSeleccionado && partes[musculoSeleccionado] && partes[musculoSeleccionado].userData.materialAntes) {
        const m = partes[musculoSeleccionado];
        const anteriorSel = m.material;
        m.material = m.userData.materialAntes;
        delete m.userData.materialAntes;
        if (anteriorSel && anteriorSel !== m.material) anteriorSel.dispose();
    }
}

function seleccionarMusculo(id) {
    restaurarSeleccion();
    if (musculoSeleccionado === id) { musculoSeleccionado = null; return; }
    const mesh = partes[id];
    if (mesh) {
        mesh.userData.materialAntes = mesh.material;
        mesh.material = crearMaterial(materialSeleccionBase);
        musculoSeleccionado = id;
    }
}

const raycaster = new THREE.Raycaster();
const mouse = new THREE.Vector2();
const popup = document.getElementById('muscle-popup');
const infoPanel = document.getElementById('info-panel');
const infoNombre = document.getElementById('info-nombre');
const infoContenido = document.getElementById('info-contenido');
let popupTimeout;

function cerrarInfo() { infoPanel.style.display = 'none'; }
window.cerrarInfo = cerrarInfo;

function buscarEjerciciosDeMusculo(idMusculo) {
    const ejercicios = { primary: [], secondary: [], stabilizers: [], articulacion: [] };
    for (const clave in baseDatos) {
        const datos = baseDatos[clave];
        for (const grupo of (datos.primary || [])) if (grupo.meshes.includes(idMusculo) && !ejercicios.primary.includes(clave)) ejercicios.primary.push(clave);
        for (const grupo of (datos.secondary || [])) if (grupo.meshes.includes(idMusculo) && !ejercicios.secondary.includes(clave)) ejercicios.secondary.push(clave);
        for (const grupo of (datos.stabilizers || [])) if (grupo.meshes.includes(idMusculo) && !ejercicios.stabilizers.includes(clave)) ejercicios.stabilizers.push(clave);
        for (const grupo of (datos.joints || [])) if (grupo.meshes.includes(idMusculo) && !ejercicios.articulacion.includes(clave)) ejercicios.articulacion.push(clave);
    }
    return ejercicios;
}

function listaConBotones(arr) {
    if (arr.length === 0) return "";
    let html = "";
    arr.forEach(e => { html += `<div class="info-lista"><button class="btn-ejercicio-mini" data-ejercicio="${e}">${e}</button></div>`; });
    return html;
}

function mostrarInfoMusculo(id) {
    const info = infoMusculos[id];
    const nombreMostrar = nombresMusculos[id] || id;
    const esArt = esArticulacion(id);
    const esEst = esEstructura(id);
    const tipoBadge = esArt ? 'tipo-articulacion' : (esEst ? 'tipo-estructura' : 'tipo-musculo');
    const tipoTexto = esArt ? 'Articulación' : (esEst ? 'Estructura' : 'Músculo');

    infoNombre.innerText = info ? info.nombre : nombreMostrar;
    let html = `<div class="tipo-badge ${tipoBadge}">${tipoTexto}</div>`;
    html += `<div class="tecnica-peso"><strong>💡 Técnica &gt; Peso</strong><br>La técnica correcta es más importante que cargar mucho peso. Con mala forma: (1) el músculo objetivo no trabaja, (2) te lesionas, (3) progresas más lento. <strong>Primero domina el movimiento, después sube el peso.</strong></div>`;

    if (info) {
        if (info.funciones) {
            html += `<div class="info-seccion"><span class="info-label">Función</span>`;
            info.funciones.forEach(f => { html += `<div class="info-lista">• ${f}</div>`; });
            html += `</div>`;
        }
        if (info.cruza) html += `<div class="info-seccion"><span class="info-label">Cruza</span><div class="info-texto">${info.cruza.join(" · ")}</div></div>`;
        if (info.ubicacion) html += `<div class="info-seccion"><span class="info-label">Ubicación</span><div class="info-texto">${info.ubicacion}</div></div>`;
    }
    const ej = buscarEjerciciosDeMusculo(id);
    if (ej.primary.length > 0) html += `<div class="info-seccion"><span class="info-label" style="color:#ff0000;">Primario en</span>${listaConBotones(ej.primary)}</div>`;
    if (ej.secondary.length > 0) html += `<div class="info-seccion"><span class="info-label" style="color:#ff8800;">Secundario en</span>${listaConBotones(ej.secondary)}</div>`;
    if (ej.stabilizers.length > 0) html += `<div class="info-seccion"><span class="info-label" style="color:#ffdd00;">Estabilizador en</span>${listaConBotones(ej.stabilizers)}</div>`;
    if (ej.articulacion.length > 0) html += `<div class="info-seccion"><span class="info-label" style="color:#00ccff;">Participa en</span>${listaConBotones(ej.articulacion)}</div>`;
    const rel = MUSCULOS_RELACIONADOS[id];
    if (rel && rel.length > 0) {
        html += `<div class="info-seccion"><span class="info-label" style="color:#88dd88;">Músculos relacionados</span>`;
        rel.forEach(r => { html += `<div class="info-lista">• ${r}</div>`; });
        html += `</div>`;
    }
    infoContenido.innerHTML = html;
    infoPanel.style.display = 'block';

    infoContenido.querySelectorAll('.btn-ejercicio-mini').forEach(btn => {
        btn.addEventListener('click', () => {
            setTexto(btn.getAttribute('data-ejercicio'));
            entrenar();
            infoPanel.style.display = 'none';
        });
    });
}

renderer.domElement.addEventListener('click', (event) => {
    const rect = renderer.domElement.getBoundingClientRect();
    mouse.x = ((event.clientX - rect.left) / rect.width) * 2 - 1;
    mouse.y = -((event.clientY - rect.top) / rect.height) * 2 + 1;
    raycaster.setFromCamera(mouse, camera);
    const partesVisibles = Object.values(partes).filter(p => p.visible);
    const intersects = raycaster.intersectObjects(partesVisibles, false);
    if (intersects.length > 0) {
        const hit = intersects[0].object;
        const idMusculo = hit.name;
        if (!partes[idMusculo]) return;

        seleccionarMusculo(idMusculo);

        const nombreMostrar = nombresMusculos[idMusculo] || idMusculo;
        popup.innerText = nombreMostrar;
        popup.style.left = (event.clientX + 15) + 'px';
        popup.style.top = (event.clientY - 15) + 'px';
        popup.style.display = 'block';
        clearTimeout(popupTimeout);
        popupTimeout = setTimeout(() => { popup.style.display = 'none'; }, 2000);

        mostrarInfoMusculo(idMusculo);
    } else {
        popup.style.display = 'none';
    }
});

function normalizar(texto) {
    return texto.toLowerCase().trim().normalize("NFD").replace(/[\u0300-\u036f]/g, "");
}

function setTexto(texto) { document.getElementById("inputEjercicio").value = texto; }

function limpiar() {
    restaurarSeleccion();
    musculoSeleccionado = null;

    Object.values(partes).forEach(parte => {
        let baseMat;
        if (esArticulacion(parte.name) || esEstructura(parte.name)) baseMat = materialHuesoBase;
        else if (esProfundo(parte.name)) baseMat = materialProfundoBase;
        else baseMat = materialMusculoBase;
        reemplazarMaterial(parte, crearMaterial(baseMat));
    });
    document.getElementById("resultado").innerHTML = "Escribe un ejercicio...";
    document.getElementById("resultado").style.color = "#aaa";
}

function aplicarMaterial(grupoMusculos, materialBase) {
    grupoMusculos.forEach(grupo => grupo.meshes.forEach(id => {
        if (partes[id]) reemplazarMaterial(partes[id], crearMaterial(materialBase));
    }));
}

function construirHTMLLista(grupoMusculos, color) {
    if (!grupoMusculos || grupoMusculos.length === 0) return "";
    let html = "";
    grupoMusculos.forEach(grupo => html += `<div class="musculo"><span style="color:${color};">■</span> ${grupo.nombre}</div>`);
    return html;
}

function rutinaCompleta() {
    limpiar();
    Object.values(partes).forEach(parte => {
        if (esMusculo(parte.name)) {
            reemplazarMaterial(parte, crearMaterial(materialPrimaryBase));
        }
    });
    const resultadoDiv = document.getElementById("resultado");
    resultadoDiv.innerHTML = `<div class="cat"><span class="cat-titulo" style="color:#ff0000;">RUTINA COMPLETA</span><div class="musculo">Todo el cuerpo activado.</div><div class="musculo" style="margin-top:6px; color:#888;">Split sugerido:</div><div class="musculo">• Lunes: Pecho + Tríceps</div><div class="musculo">• Martes: Espalda + Bíceps</div><div class="musculo">• Miércoles: Piernas</div><div class="musculo">• Jueves: Hombros + Core</div><div class="musculo">• Viernes: Full body</div></div>`;
    resultadoDiv.style.color = "#aaa";
}

function entrenar() {
    limpiar();
    const input = normalizar(document.getElementById("inputEjercicio").value);
    let ejercicioEncontrado = null;
    const aliasOrdenados = [];
    for (const clave in baseDatos) baseDatos[clave].alias.forEach(alias => aliasOrdenados.push({ aliasNorm: normalizar(alias), clave }));
    aliasOrdenados.sort((a, b) => b.aliasNorm.length - a.aliasNorm.length);
    for (const entrada of aliasOrdenados) if (input === entrada.aliasNorm) { ejercicioEncontrado = baseDatos[entrada.clave]; break; }
    if (!ejercicioEncontrado) {
        for (const entrada of aliasOrdenados) {
            const aliasEscapado = entrada.aliasNorm.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
            const regex = new RegExp(`(^|\\s)${aliasEscapado}(\\s|$)`);
            if (regex.test(input)) { ejercicioEncontrado = baseDatos[entrada.clave]; break; }
        }
    }
    const resultadoDiv = document.getElementById("resultado");
    resultadoDiv.style.color = "#aaa";
    if (ejercicioEncontrado) {
        aplicarMaterial(ejercicioEncontrado.primary || [], materialPrimaryBase);
        aplicarMaterial(ejercicioEncontrado.secondary || [], materialSecondaryBase);
        aplicarMaterial(ejercicioEncontrado.stabilizers || [], materialStabilizerBase);
        aplicarMaterial(ejercicioEncontrado.joints || [], materialJointBase);
        let html = "";
        if (ejercicioEncontrado.primary?.length) html += `<div class="cat"><span class="cat-titulo" style="color:#ff0000;">PRIMARIOS</span>${construirHTMLLista(ejercicioEncontrado.primary, '#ff0000')}</div>`;
        if (ejercicioEncontrado.secondary?.length) html += `<div class="cat"><span class="cat-titulo" style="color:#ff8800;">SECUNDARIOS</span>${construirHTMLLista(ejercicioEncontrado.secondary, '#ff8800')}</div>`;
        if (ejercicioEncontrado.stabilizers?.length) html += `<div class="cat"><span class="cat-titulo" style="color:#ffdd00;">ESTABILIZADORES</span>${construirHTMLLista(ejercicioEncontrado.stabilizers, '#ffdd00')}</div>`;
        if (ejercicioEncontrado.joints?.length) html += `<div class="cat"><span class="cat-titulo" style="color:#00ccff;">ARTICULACIONES</span>${construirHTMLLista(ejercicioEncontrado.joints, '#00ccff')}</div>`;
        if (ejercicioEncontrado.movement) html += `<div class="movimiento"><span class="cat-titulo" style="color:#fff;">MOVIMIENTO</span><div class="musculo">↑ ${ejercicioEncontrado.movement.subida}</div><div class="musculo">↓ ${ejercicioEncontrado.movement.bajada}</div></div>`;
        resultadoDiv.innerHTML = html;
    } else {
        resultadoDiv.innerText = "No reconocido. Escribe un ejercicio válido.";
        resultadoDiv.style.color = "#ff4444";
    }
}

function togglePanel() {
    const panel = document.getElementById("panelControl");
    const btn = document.getElementById("toggle-btn");
    if (panel.style.display === "none" || panel.style.display === "") {
        panel.style.display = "block"; btn.innerText = "Ocultar Menú";
    } else {
        panel.style.display = "none"; btn.innerText = "Mostrar Menú";
    }
}

function renderizarBotones() {
    const cont = document.getElementById("listaBotones");
    cont.innerHTML = "";
    const grupos = {};
    const nombresGrupos = { mancuerna: "MANCUERNAS", barra: "BARRA", maquina: "MÁQUINAS", cuerpo: "PESO CORPORAL" };

    for (const clave in baseDatos) {
        const datos = baseDatos[clave];
        if (filtroEquipo !== 'todos' && datos.tipo !== filtroEquipo) continue;
        if (filtroGrupo !== 'todos' && obtenerGrupoMuscular(datos) !== filtroGrupo) continue;
        const tipo = datos.tipo || "cuerpo";
        if (!grupos[tipo]) grupos[tipo] = [];
        grupos[tipo].push(clave);
    }

    const orden = ["mancuerna", "barra", "maquina", "cuerpo"];
    let total = 0;
    orden.forEach(t => {
        if (grupos[t] && grupos[t].length > 0) {
            const tituloEl = document.createElement("div");
            tituloEl.className = "seccion-titulo";
            tituloEl.innerText = nombresGrupos[t] || t.toUpperCase();
            cont.appendChild(tituloEl);
            grupos[t].forEach(clave => {
                const btn = document.createElement("button");
                btn.className = "btn-ejemplo";
                btn.innerText = clave;
                btn.addEventListener("click", () => { setTexto(clave); entrenar(); });
                cont.appendChild(btn);
                total++;
            });
        }
    });

    if (total === 0) {
        const vacio = document.createElement("div");
        vacio.className = "seccion-titulo";
        vacio.innerText = "Sin ejercicios para este filtro";
        cont.appendChild(vacio);
    }
}

const inputMusculo = document.getElementById('inputMusculo');
const sugerenciasDiv = document.getElementById('sugerenciasMusculo');
const nombresMusculosNormalizados = {};
Object.keys(nombresMusculos).forEach(id => {
    nombresMusculosNormalizados[id] = normalizar(nombresMusculos[id]);
});

function buscarMusculos(texto) {
    const q = normalizar(texto);
    if (q.length < 2) return [];
    const resultados = [];
    for (const id in nombresMusculos) {
        const nombreNorm = nombresMusculosNormalizados[id];
        if (nombreNorm.includes(q)) {
            const tipo = esArticulacion(id) ? 'Articulación' : (esEstructura(id) ? 'Estructura' : 'Músculo');
            resultados.push({ id, nombre: nombresMusculos[id], tipo, prioridad: nombreNorm.indexOf(q) });
        }
    }
    resultados.sort((a, b) => a.prioridad - b.prioridad || a.nombre.length - b.nombre.length);
    return resultados.slice(0, 12);
}

function mostrarSugerencias() {
    const texto = inputMusculo.value.trim();
    sugerenciasDiv.innerHTML = "";
    if (texto.length < 2) return;

    const resultados = buscarMusculos(texto);
    if (resultados.length === 0) {
        sugerenciasDiv.innerHTML = '<div class="sugerencia-vacia">Sin resultados</div>';
        return;
    }

    resultados.forEach(r => {
        const div = document.createElement('div');
        div.className = 'sugerencia-item';
        div.innerHTML = `<span>${r.nombre}</span><span class="sug-tipo">${r.tipo}</span>`;
        div.addEventListener('click', () => {
            seleccionarMusculo(r.id);
            mostrarInfoMusculo(r.id);
            inputMusculo.value = "";
            sugerenciasDiv.innerHTML = "";
        });
        sugerenciasDiv.appendChild(div);
    });
}

inputMusculo.addEventListener('input', mostrarSugerencias);
inputMusculo.addEventListener('focus', mostrarSugerencias);
document.addEventListener('click', (e) => {
    if (!inputMusculo.contains(e.target) && !sugerenciasDiv.contains(e.target)) {
        sugerenciasDiv.innerHTML = "";
    }
});

document.getElementById("toggle-btn").addEventListener("click", togglePanel);
document.getElementById("btnEntrenar").addEventListener("click", entrenar);
const btnRC = document.getElementById("btnRutinaCompleta");
if (btnRC) btnRC.addEventListener("click", rutinaCompleta);
document.getElementById("inputEjercicio").addEventListener("keypress", function(event) { if (event.key === "Enter") entrenar(); });

document.querySelectorAll(".filtro-btn").forEach(btn => btn.addEventListener("click", function() {
    document.querySelectorAll(".filtro-btn").forEach(b => b.classList.remove("activo"));
    this.classList.add("activo");
    filtroEquipo = this.getAttribute("data-filtro");
    renderizarBotones();
}));

document.querySelectorAll(".grupo-btn").forEach(btn => btn.addEventListener("click", function() {
    document.querySelectorAll(".grupo-btn").forEach(b => b.classList.remove("activo"));
    this.classList.add("activo");
    filtroGrupo = this.getAttribute("data-grupo");
    renderizarBotones();
}));

document.getElementById("legend-help").addEventListener("click", function(e) {
    e.stopPropagation();
    const modal = document.getElementById("legend-modal");
    modal.style.display = modal.style.display === "block" ? "none" : "block";
});

const leyendaEl = document.getElementById("leyendaFlotante");
let isDraggingLegend = false;
let startX, startY, initialLeft, initialTop;

function iniciarArrastre(clientX, clientY) {
    const rect = leyendaEl.getBoundingClientRect();
    isDraggingLegend = true;
    startX = clientX;
    startY = clientY;
    initialLeft = rect.left;
    initialTop = rect.top;
    leyendaEl.style.transform = 'none';
    leyendaEl.style.left = rect.left + 'px';
    leyendaEl.style.top = rect.top + 'px';
    leyendaEl.style.bottom = 'auto';
}
function moverArrastre(clientX, clientY) {
    if (!isDraggingLegend) return;
    const dx = clientX - startX;
    const dy = clientY - startY;
    leyendaEl.style.left = (initialLeft + dx) + 'px';
    leyendaEl.style.top = (initialTop + dy) + 'px';
}
function soltarArrastre() { isDraggingLegend = false; }

leyendaEl.addEventListener('mousedown', (e) => {
    if (e.target.tagName === 'BUTTON') return;
    e.preventDefault();
    iniciarArrastre(e.clientX, e.clientY);
});
document.addEventListener('mousemove', (e) => moverArrastre(e.clientX, e.clientY));
document.addEventListener('mouseup', soltarArrastre);
leyendaEl.addEventListener('touchstart', (e) => {
    if (e.target.tagName === 'BUTTON') return;
    const t = e.touches[0];
    iniciarArrastre(t.clientX, t.clientY);
}, {passive: true});
document.addEventListener('touchmove', (e) => {
    if (!isDraggingLegend) return;
    const t = e.touches[0];
    moverArrastre(t.clientX, t.clientY);
}, {passive: true});
document.addEventListener('touchend', soltarArrastre);

renderizarBotones();

function animate() {
    requestAnimationFrame(animate);
    controls.update();
    renderer.render(scene, camera);
}
animate();

window.addEventListener('resize', () => {
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, window.innerHeight);
});
