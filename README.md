# jhntwain
Authoring App
Grok report 1 2 and 3 of the personal files of this project demonstrate hopefully most of the projects scope I hope to pursue with you .. I would like to now use HTML5 code to draft a version 0.0.01
please generate a single file interactive
Goal: Code File Architecture/Structure
Code Requirements:
Suggestions to obtain DRY IIFE Object Oriented best practices :
Custom Abbrev that maintains full Readability naming convnxn: remove vowels except when: the word is less than 4 letters long; vowel is the first letter in the word; vowel has a constant on either side; vowel is adjacent to another vowel. use known abbrev like pls for please and r for are
cssregistry that serves as a datastructure that stores all css prop names in a single array/vector. and maps dom elements/classes/ids to a double array [[csspropnameindxs][csspropvalues]]
use helper functions to reduce repeated function calls/repeated scriptlets : example would be an appendChildren(prntElmnt, chldElmnt1, chldElmnt2, etc);
html should contain only a single root element inside the body so that all other DOM can "plug in" to the root element
DO NOT EVER use innerHtml as it is a security vulnerability
DO NOT EVER have styling names somewhere other than the cssregistry.
have a css prop name for css somewhere other than the cssregistry
Data Driven Module IIFE Architecture Draft v 0.0.01
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
<title>JhnTwain 0.0.01</title>
<style id="jtwGlobalStyles"></style>
</head>
<body>
<div id="root"></div>

<script>

// UTILITIES LAYER

const Utils = (function(){

const cssRgstry = {props:[],map:new Map()}

function crtEl(tag,cls,txt){}

function appndChld(prnt,...chlds){}

function clrChld(el){}

function regCss(el,styleObj){}

function pub(topic,data){}

function sub(topic,fn){}

function saveToStore(key,val){}

function loadFromStore(key){}

function dragInit(el,callbacks){}

return {crtEl,appndChld,clrChld,regCss,pub,sub,saveToStore,loadFromStore,dragInit,cssRgstry}

})()



const AppPlugins = (function(){

function createCardBase(ent){}

function parseTextToEntities(txt){}

function drawLink(src,tgt,typ){}

function showModal(content,actions){}

return {createCardBase,parseTextToEntities,drawLink,showModal}

})()



// CORE APPLICATION

const JhnTwain = (function(){



const JhnTwainState = (function(){

let data = {
seed:{title:"",target:0,theme:"",premise:"",seedTxt:""},
entities:new Map(),
proseBlks:[],
relations:[],
harmny:{conductor:{},narrTrain:{},multiverse:{}}
}

function get(){}

function set(path,val){}

function addEnt(ty,init){}

function updEnt(id,changes){}

function getEntsByTy(ty){}

function subscribe(fn){}

return {get,set,addEnt,updEnt,getEntsByTy,subscribe}

})()



const JhnTwainUIX = (function(U,S){

function regAllCss(){}

function buildHeader(){}

function buildTabBar(){}

function buildSeedPnl(){}

function buildProsePnl(){}

function buildCharPnl(){}

function buildWrkspPnl(){}

function buildHarmnyPnl(){}

function buildExportPnl(){}

function renderEntityCard(ent){}

function refreshAll(){}

function buildUI(){}

return {buildUI,renderEntityCard,refreshAll}

})(Utils,JhnTwainState)



const JhnTwainCore = (function(S,U){

function init(){}

function handleAction(action,payload){}

function syncUI(){}

function autoSave(){}

return {init,handleAction,syncUI}

})(JhnTwainState,JhnTwainUIX)



const EntityMgr = (function(S){

const entTypes = {
char:{prefix:"@char",defaults:["name","aspect"],color:"#0ca"},
scene:{prefix:"@scene",defaults:["time","prose"]},
conflict:{prefix:"@conflict",defaults:["type","magnitude","state"]},
research:{prefix:"@research",defaults:["topic","notes"]},
storycard:{prefix:"@card",defaults:["content","attachedTo"]},
thread:{prefix:"@thread",defaults:["name","motif"]},
conductor:{prefix:"@conductor",defaults:["harmony","tempo"],singleton:true},
narrTrain:{prefix:"@train",defaults:["momentum","nextBeat"],singleton:true},
multiverse:{prefix:"@multiverse",defaults:["branches","violations"],singleton:true}
}

function crtEnt(ty,initData){}

function updAttr(id,attrPath,val){}

function getByTy(ty){}

function getById(id){}

function delEnt(id){}

function lnkEnts(srcId,tgtId,lnkTy){}

function toEAS(){}

function fromEAS(txt){}

function addCustomTy(newTyCfg){}

function valAttr(ent,attr,val){}

return {
crtEnt,
updAttr,
getByTy,
getById,
delEnt,
lnkEnts,
toEAS,
fromEAS,
addCustomTy,
valAttr
}

})(JhnTwainState)



const StorySeed = (function(S){

function updSeed(field,val){}

function getSeed(){}

return {updSeed,getSeed}

})(JhnTwainState)



const ProseEngine = (function(S){

function saveProse(txt){}

function getManuscript(){}

function applySymphony(blockId,attrs){}

return {saveProse,getManuscript,applySymphony}

})(JhnTwainState)



const HarmonyLayer = (function(S){

function getConductor(){}

function getNarrativeTrain(){}

function checkConsistency(){}

function suggestNext(){}

return {getConductor,getNarrativeTrain,checkConsistency,suggestNext}

})(JhnTwainState)



const Workspace = (function(S,U){

function renderCanvas(){}

function handleCardDrop(id,x,y){}

function updateCardPos(id,x,y){}

function renderLinks(){}

return {renderCanvas,handleCardDrop,updateCardPos,renderLinks}

})(JhnTwainState,JhnTwainUIX)



const ExportMgr = (function(S){

function exportEAS(){}

function exportManuscript(){}

function importEAS(txt){}

return {exportEAS,exportManuscript,importEAS}

})(JhnTwainState)



function init(){
JhnTwainUIX.buildUI()
JhnTwainCore.init()
}



return {init,EntityMgr,StorySeed,ProseEngine,HarmonyLayer,Workspace,ExportMgr}

})()



JhnTwain.init()

</script>
</body>
</html>


Use a single space per indentation and use no other char or set of characters for indentations.
do not use multiple "--","__" or any other way to section/comment/announce/etc in the code file itself.. if seperation of a section is evaluated as important to structure or readability then use 2 return characters

