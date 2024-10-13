Data files
A data file is an entry in the resource manifest that references a file to load in the game extra content mounting system.

Data file types
Key	File type	Root element	Mounter	Example
ACTION_TABLE_DEFINITIONS			CActionInfoDataFileMounter	
ALTERNATE_VARIATIONS_FILE			CPedVariationStreamFileMounter	dlc_mpbattlecrc:/common/data/pedalternatevariations.meta
AMB_PROCEDURAL_BLOOD_FILE			CVFXBloodFileMounter	
AMBIENT_PED_MODEL_SET_FILE			AmbientModelSetMounter	
AMBIENT_PROP_MODEL_SET_FILE			AmbientModelSetMounter	
AMBIENT_VEHICLE_MODEL_SET_FILE			AmbientModelSetMounter	
AUDIO_CURVEDATA			audMetadataDataFileMounter	
AUDIO_DYNAMIXDATA			audMetadataDataFileMounter	
AUDIO_GAMEDATA			audMetadataDataFileMounter	x64:/audio/audio_rel/config/game.dat151.rel
AUDIO_SOUNDDATA			audMetadataDataFileMounter	x64:/audio/audio_rel/config/sounds.dat54.rel
AUDIO_SPEECHDATA			audSpeechDataFileMounter	x64:/audio/audio_rel/config/dlc_gtao_speech.dat4.rel
AUDIO_SYNTHDATA			audMetadataDataFileMounter	
AUDIO_WAVEPACK	Folder containing wave packs	N/A	audWavePackDataFileMounter	dlcmpheist:/x64/audio/sfx/
CARCOLS_FILE	Vehicle model variation data	CVehicleModelInfoVarGlobal	CVehicleColorsDataFileMounter	dlcmpheist:/common/data/carcols.meta
CLIP_SETS_FILE			CExtraContentFileMounter	dlc_mpbattle:/common/data/anim/clip_sets/clip_sets.xml
COMBAT_BEHAVIOUR_OVERRIDE_FILE			CCombatInfoDataFileMounter	common:/data/ai/combatbehaviour.meta
CONDITIONAL_ANIMS_FILE			ConditionalAnimationsMounter	dlcmpheist:/common/data/ai/conditionalanims.meta
CONTENT_UNLOCKING_META_FILE			CExtraContentFileMounter	
DLC_ITYP_REQUEST	Equivalent of PERMANENT_ITYP_FILE in level metas	N/A	CDLCItypFileMounter	dummy/v_common.ityp
DLC_POP_GROUPS	Population groups	CPopGroupList	CPopulationDataFileMounter	x64a:/data/popgroups.ymt, Xbox 360 popgroups.meta
DLC_SCRIPT_METAFILE			CDLCScriptDataMounter	
DLC_WEAPON_PICKUPS			CPickupDataManagerMounter	dlc_mpchristmas2018crc:/common/data/pickups.meta
DRIVER_RULES_STD_FILE			ScenarioInfoMounter	
EVENTS_OVERRIDE_FILE	Ped event metadata	CEventDataManager	CEventDataFileMounter	common:/data/events.meta
EXPLOSION_INFO_FILE		CExplosionInfoManager	CExplosionFileMounter	dlc_mpchristmas2017crc:/common/data/explosion.meta
EXPLOSIONFX_FILE			CVfxExplosionFileMounter	
EXPRESSION_SETS_FILE			CExtraContentFileMounter	
EXTRA_FOLDER_MOUNT_DATA			CExtraContentFileMounter	
EXTRA_TITLE_UPDATE_DATA			CExtraContentFileMounter	
FACIAL_CLIPSET_GROUPS_FILE			CExtraContentFileMounter	
GTXD_PARENTING_DATA	TXD parent/child relationships for maps	CMapParentTxds	CExtraContentFileMounter	dlcmpheist:/common/data/gtxd.meta
HANDLING_FILE	Handling data XML	CHandlingDataMgr	CVehicleHandlingFileMounter	dlcmpheist:/common/data/handling.meta
INTERIOR_PROXY_ORDER_FILE			CInteriorProxyFileMounter	dlc_mpgunrunning:/common/data/interiorproxies.meta
LEVEL_STREAMING_FILE			CExtraContentFileMounter	
LOADOUTS_FILE		CPedInventoryLoadOutManager	CExtraContentFileMounter	dlc_mpgunrunningcrc:/common/data/ai/loadouts.meta
MOVE_NETWORK_DEFS		fwMoveNetworkDefs	CExtraContentFileMounter	dlcmpheist:/common/data/anim/networkdefs.meta
MP_STATS_DISPLAY_LIST_FILE			CStatsDisplayListFileMounter	
MP_STATS_UI_LIST_FILE			CStatsUIListFileMounter	
NM_TUNING_FILE			CExtraContentFileMounter	
OVERLAY_INFO_FILE			CExtraContentFileMounter	dlc_mpbattle:/common/data/overlayinfo.xml
PED_BOUNDS_FILE			CPedModelMetaDataFileMounter	
PED_BRAWLING_STYLE_FILE			CBrawlingStyleMetaDataFileMounter	
PED_COMPONENT_SETS_FILE			CPedModelMetaDataFileMounter	
PED_DAMAGE_APPEND_FILE			CPedDamageDataMounter	dlcmpheist:/common/data/effects/peds/peddamage.xml
PED_DAMAGE_OVERRIDE_FILE			CPedDamageDataMounter	
PED_FIRST_PERSON_ALTERNATE_DATA			CPedVariationStreamFileMounter	
PED_FIRST_PERSON_ASSET_DATA			CPedVariationStreamFileMounter	dlc_mpbattle:/common/data/effects/peds/first_person.meta
PED_METADATA_FILE			CPedModelMetaDataFileMounter	dlcgunrunning:/common/data/peds.meta
PED_OVERLAY_FILE			CPedDecorationsDataFileMounter	dlcmpheistcrc:/common/data/effects/peds/mpheist_overlays.xml
PED_PERCEPTION_FILE			CPedModelMetaDataFileMounter	
PED_PERSONALITY_FILE			CPedModelMetaDataFileMounter	dlcgunrunning:/common/data/pedpersonality.meta
PED_TASK_DATA_FILE			CPedModelMetaDataFileMounter	
PEDSTREAM_FILE			CPedVariationStreamFileMounter	
POPSCHED_FILE	Population scheduling data override	N/A	CPopulationDataFileMounter	common:/data/levels/gta5/popcycle.dat
PTFXASSETINFO_FILE			CVisualEffectsFileMounter	dlc_mpchristmas2017:/common/data/effects/ptfxassetinfo.meta
SCALEFORM_DLC_FILE			CScaleformPreallocationDataFileMounter	
SCALEFORM_PREALLOC_FILE			CScaleformPreallocationDataFileMounter	
SCENARIO_INFO_FILE			ScenarioInfoMounter	dlcmpheist:/common/data/ai/scenarios.meta
SCENARIO_POINTS_FILE			ScenarioPointMounter	
SCENARIO_POINTS_OVERRIDE_FILE			ScenarioPointMounter	
SCENARIO_POINTS_PSO_FILE			ScenarioPointMounter	
SCENARIO_POINTS_OVERRIDE_PSO_FILE	Scenario Points Manifest	CScenarioPointManifest	ScenarioPointMounter	x64a:/levels/gta5/sp_manifest.ymt
SCRIPT_BRAIN_FILE			CScriptBrainFileMounter	
SCRIPTFX_FILE			CVFXScriptFileMounter	
SHOP_PED_APPAREL_META_FILE			CExtraMetaDataFileMounter	dlc_mpimportexport:/common/data/mp_m_freemode_01_impexp_shop.meta
SP_STATS_DISPLAY_LIST_FILE			CStatsDisplayListFileMounter	
SP_STATS_UI_LIST_FILE			CStatsUIListFileMounter	
STREAMING_REQUEST_LISTS_FILE			SRLMounter	dlcmpheist:/common/data/srllist.meta
TATTOO_SHOP_DLC_FILE			CExtraMetaDataFileMounter	dlc_mpchristmas2018crc:/common/data/shop_tattoo.meta
TEXTFILE_METAFILE			CExtraContentFileMounter	
TIMECYCLEMOD_FILE	Timecycle Mod		TimeCycleFileMounter	common:/data/timecycle/timecycle_mods_1.xml
TRAINCONFIGS_FILE	Train config		CTrainConfigFileMounter	common:/data/levels/gta5/trains.xml
TRAINTRACK_FILE	Train tracks		CTrainConfigFileMounter	common:/data/levels/gta5/traintracks.xml
VEHICLE_LAYOUTS_FILE			CVehicleMetadataFileMounter	dlc_mpsmugglercrc:/common/data/ai/vehiclelayouts.meta
VEHICLE_METADATA_FILE			CVehicleMetaDataFileMounter	dlc_mpchristmas2018crc:/common/data/levels/gta5/vehicles.meta
VEHICLE_SHOP_DLC_FILE			CExtraContentFileMounter	dlc_mpchristmas2018crc:/common/data/shop_vehicle.meta
VEHICLE_VARIATION_FILE			CVehicleVariationDataFileMounter	dlc_mpchristmas2018:/common/data/carvariations.meta
VEHICLEEXTRAS_FILE			CVehicleExtrasFileMounter	common:/data/vehicleextras.dat
VFXVEHICLEINFO_FILE			CVfxVehicleInfoFileMounter	x64w:/dlcpacks/mppilot/dlc/common/data/effects/vfxvehicleinfo.meta
WEAPON_ANIMATIONS_FILE			CWeaponAnimationsDataFileMounter	dlc_mpbikercrc:/common/data/ai/weaponanimations.meta
WEAPON_METADATA_FILE			CWeaponMetaDataFileMounter	dlcmphalloweencrc:/common/data/weaponarchetypes.meta
WEAPON_SHOP_INFO_METADATA_FILE			CExtraMetaDataFileMounter	
WEAPONCOMPONENTSINFO_FILE			CWeaponComponentDataFileMounter	dlc_mpbikercrc:/common/data/ai/weaponcomponents.meta
WEAPONINFO_FILE_PATCH			CWeaponInfoDataFileMounter	
WEAPONINFO_FILE			CWeaponInfoDataFileMounter	dlc_mpbikercrc:/common/data/ai/weaponpipebomb.meta
ZONEBIND_FILE		CPopZoneData	CPopulationDataFileMounter	x64a:/levels/gta5/zonebind.ymt
FIVEM_LOVES_YOU_447B37BE29496FA0			CExtraContentFileMounter	
FIVEM_LOVES_YOU_1F764C843460150			CIplCullboxFileMounter	
FIVEM_LOVES_YOU_9605D14551590909			CPopulationDataFileMounter

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

Game events
This is a list of low-level game events. That means, these are the events that come straight from GTA V's core mechanics. Using these events can be useful when you need fine control over what happens in your scripts. See gameEventTriggered for more information on how to use these events.

Note that this list is largely undocumented and you probably won't need most of the events listed here. If you have useful information to share, please add it to this doc. Any help is greatly appreciated!

Event name	Description
CEventAcquaintancePed	
CEventAcquaintancePedDead	
CEventAcquaintancePedDislike	
CEventAcquaintancePedHate	
CEventAcquaintancePedLike	
CEventAcquaintancePedWanted	
CEventAgitated	
CEventAgitatedAction	
CEventCallForCover	
CEventCarUndriveable	
CEventClimbLadderOnRoute	
CEventClimbNavMeshOnRoute	
CEventCombatTaunt	
CEventCommunicateEvent	
CEventCopCarBeingStolen	
CEventCrimeCryForHelp	
CEventCrimeReported	
CEventDamage	
CEventDataDecisionMaker	
CEventDataFileMounter	
CEventDataResponseAggressiveRubberneck	
CEventDataResponseDeferToScenarioPointFlags	
CEventDataResponseFriendlyAimedAt	
CEventDataResponseFriendlyNearMiss	
CEventDataResponsePlayerDeath	
CEventDataResponsePoliceTaskWanted	
CEventDataResponseSwatTaskWanted	
CEventDataResponseTask	
CEventDataResponseTaskAgitated	
CEventDataResponseTaskCombat	
CEventDataResponseTaskCower	
CEventDataResponseTaskCrouch	
CEventDataResponseTaskDuckAndCover	
CEventDataResponseTaskEscapeBlast	
CEventDataResponseTaskEvasiveStep	
CEventDataResponseTaskExhaustedFlee	
CEventDataResponseTaskExplosion	
CEventDataResponseTaskFlee	
CEventDataResponseTaskFlyAway	
CEventDataResponseTaskGrowlAndFlee	
CEventDataResponseTaskGunAimedAt	
CEventDataResponseTaskHandsUp	
CEventDataResponseTaskHeadTrack	
CEventDataResponseTaskLeaveCarAndFlee	
CEventDataResponseTaskScenarioFlee	
CEventDataResponseTaskSharkAttack	
CEventDataResponseTaskShockingEventBackAway	
CEventDataResponseTaskShockingEventGoto	
CEventDataResponseTaskShockingEventHurryAway	
CEventDataResponseTaskShockingEventReact	
CEventDataResponseTaskShockingEventReactToAircraft	
CEventDataResponseTaskShockingEventStopAndStare	
CEventDataResponseTaskShockingEventThreatResponse	
CEventDataResponseTaskShockingEventWatch	
CEventDataResponseTaskShockingNiceCar	
CEventDataResponseTaskShockingPoliceInvestigate	
CEventDataResponseTaskThreat	
CEventDataResponseTaskTurnToFace	
CEventDataResponseTaskWalkAway	
CEventDataResponseTaskWalkRoundEntity	
CEventDataResponseTaskWalkRoundFire	
CEventDeadPedFound	
CEventDeath	
CEventDecisionMakerResponse	
CEventDisturbance	
CEventDraggedOutCar	
CEventEditableResponse	
CEventEncroachingPed	
CEventEntityDamaged	
CEventEntityDestroyed	
CEventExplosion	
CEventExplosionHeard	
CEventFireNearby	
CEventFootStepHeard	
CEventFriendlyAimedAt	
CEventFriendlyFireNearMiss	
CEventGetOutOfWater	
CEventGivePedTask	
CEventGroupScriptAI	
CEventGroupScriptNetwork	
CEventGunAimedAt	
CEventGunShot	
CEventGunShotBulletImpact	
CEventGunShotWhizzedBy	
CEventHelpAmbientFriend	
CEventHurtTransition	
CEventInAir	
CEventInfo	
CEventInfoBase	
CEventInjuredCryForHelp	
CEventLeaderEnteredCarAsDriver	
CEventLeaderExitedCarAsDriver	
CEventLeaderHolsteredWeapon	
CEventLeaderLeftCover	
CEventLeaderUnholsteredWeapon	
CEventMeleeAction	
CEventMustLeaveBoat	
CEventNetworkAdminInvited	
CEventNetworkAttemptHostMigration	
CEventNetworkBail	
CEventNetworkCashTransactionLog	
CEventNetworkCheatTriggered	
CEventNetworkClanInviteReceived	
CEventNetworkClanJoined	
CEventNetworkClanKicked	
CEventNetworkClanLeft	
CEventNetworkClanRankChanged	
CEventNetworkCloudEvent	
CEventNetworkCloudFileResponse	
CEventNetworkEmailReceivedEvent	
CEventNetworkEndMatch	
CEventNetworkEndSession	
CEventNetworkEntityDamage	
CEventNetworkFindSession	
CEventNetworkFollowInviteReceived	
CEventNetworkHostMigration	
CEventNetworkHostSession	
CEventNetworkIncrementStat	
CEventNetworkInviteAccepted	
CEventNetworkInviteConfirmed	
CEventNetworkInviteRejected	
CEventNetworkJoinSession	
CEventNetworkJoinSessionResponse	
CEventNetworkOnlinePermissionsUpdated	
CEventNetworkPedLeftBehind	
CEventNetworkPickupRespawned	
CEventNetworkPlayerArrest	
CEventNetworkPlayerCollectedAmbientPickup	
CEventNetworkPlayerCollectedPickup	
CEventNetworkPlayerCollectedPortablePickup	
CEventNetworkPlayerDroppedPortablePickup	
CEventNetworkPlayerJoinScript	
CEventNetworkPlayerLeftScript	
CEventNetworkPlayerScript	
CEventNetworkPlayerSession	
CEventNetworkPlayerSpawn	
CEventNetworkPresenceInvite	
CEventNetworkPresenceInviteRemoved	
CEventNetworkPresenceInviteReply	
CEventNetworkPresenceTriggerEvent	
CEventNetworkPresence_StatUpdate	
CEventNetworkPrimaryClanChanged	
CEventNetworkRequestDelay	
CEventNetworkRosChanged	
CEventNetworkScAdminPlayerUpdated	
CEventNetworkScAdminReceivedCash	
CEventNetworkScriptEvent	
CEventNetworkSessionEvent	
CEventNetworkShopTransaction	
CEventNetworkSignInStateChanged	
CEventNetworkSocialClubAccountLinked	
CEventNetworkSpectateLocal	
CEventNetworkStartMatch	
CEventNetworkStartSession	
CEventNetworkStorePlayerLeft	
CEventNetworkSummon	
CEventNetworkSystemServiceEvent	
CEventNetworkTextMessageReceived	
CEventNetworkTimedExplosion	
CEventNetworkTransitionEvent	
CEventNetworkTransitionGamerInstruction	
CEventNetworkTransitionMemberJoined	
CEventNetworkTransitionMemberLeft	
CEventNetworkTransitionParameterChanged	
CEventNetworkTransitionStarted	
CEventNetworkTransitionStringChanged	
CEventNetworkVehicleUndrivable	
CEventNetworkVoiceConnectionRequested	
CEventNetworkVoiceConnectionResponse	
CEventNetworkVoiceConnectionTerminated	
CEventNetworkVoiceSessionEnded	
CEventNetworkVoiceSessionStarted	
CEventNetworkWithData	
CEventNetwork_InboxMsgReceived	
CEventNewTask	
CEventObjectCollision	
CEventOnFire	
CEventOpenDoor	
CEventPedCollisionWithPed	
CEventPedCollisionWithPlayer	
CEventPedEnteredMyVehicle	
CEventPedJackingMyVehicle	
CEventPedOnCarRoof	
CEventPedSeenDeadPed	
CEventPlayerCollisionWithPed	
CEventPlayerDeath	
CEventPlayerUnableToEnterVehicle	
CEventPotentialBeWalkedInto	
CEventPotentialBlast	
CEventPotentialGetRunOver	
CEventPotentialWalkIntoVehicle	
CEventProvidingCover	
CEventRanOverPed	
CEventReactionEnemyPed	
CEventReactionInvestigateDeadPed	
CEventReactionInvestigateThreat	
CEventRequestHelp	
CEventRequestHelpWithConfrontation	
CEventRespondedToThreat	
CEventScanner	
CEventScenarioForceAction	
CEventScriptCommand	
CEventScriptWithData	
CEventShocking	
CEventShockingBicycleCrash	
CEventShockingBicycleOnPavement	
CEventShockingCarAlarm	
CEventShockingCarChase	
CEventShockingCarCrash	
CEventShockingCarOnCar	
CEventShockingCarPileUp	
CEventShockingDangerousAnimal	
CEventShockingDeadBody	
CEventShockingDrivingOnPavement	
CEventShockingEngineRevved	
CEventShockingExplosion	
CEventShockingFire	
CEventShockingGunFight	
CEventShockingGunshotFired	
CEventShockingHelicopterOverhead	
CEventShockingHornSounded	
CEventShockingInDangerousVehicle	
CEventShockingInjuredPed	
CEventShockingMadDriver	
CEventShockingMadDriverBicycle	
CEventShockingMadDriverExtreme	
CEventShockingMugging	
CEventShockingNonViolentWeaponAimedAt	
CEventShockingParachuterOverhead	
CEventShockingPedKnockedIntoByPlayer	
CEventShockingPedRunOver	
CEventShockingPedShot	
CEventShockingPlaneFlyby	
CEventShockingPotentialBlast	
CEventShockingPropertyDamage	
CEventShockingRunningPed	
CEventShockingRunningStampede	
CEventShockingSeenCarStolen	
CEventShockingSeenConfrontation	
CEventShockingSeenGangFight	
CEventShockingSeenInsult	
CEventShockingSeenMeleeAction	
CEventShockingSeenNiceCar	
CEventShockingSeenPedKilled	
CEventShockingSiren	
CEventShockingStudioBomb	
CEventShockingVehicleTowed	
CEventShockingVisibleWeapon	
CEventShockingWeaponThreat	
CEventShockingWeirdPed	
CEventShockingWeirdPedApproaching	
CEventShoutBlockingLos	
CEventShoutTargetPosition	
CEventShovePed	
CEventSoundBase	
CEventStatChangedValue	
CEventStaticCountReachedMax	
CEventStuckInAir	
CEventSuspiciousActivity	
CEventSwitch2NM	
CEventUnidentifiedPed	
CEventVehicleCollision	
CEventVehicleDamage	
CEventVehicleDamageWeapon	
CEventVehicleOnFire	
CEventWrithe

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

HUD colors
This page lists the default HUD colors as defined in common:/data/ui/hudcolor.dat, which can be overridden or obtained using the following native commands:

GET_HUD_COLOUR
REPLACE_HUD_COLOUR
REPLACE_HUD_COLOUR_WITH_RGBA
List of default colors
Color	Index	Name	RGBA
 	0	HUD_COLOUR_PURE_WHITE	rgba(255, 255, 255, 255)
 	1	HUD_COLOUR_WHITE	rgba(240, 240, 240, 255)
 	2	HUD_COLOUR_BLACK	rgba(0, 0, 0, 255)
 	3	HUD_COLOUR_GREY	rgba(155, 155, 155, 255)
 	4	HUD_COLOUR_GREYLIGHT	rgba(205, 205, 205, 255)
 	5	HUD_COLOUR_GREYDARK	rgba(77, 77, 77, 255)
 	6	HUD_COLOUR_RED	rgba(224, 50, 50, 255)
 	7	HUD_COLOUR_REDLIGHT	rgba(240, 153, 153, 255)
 	8	HUD_COLOUR_REDDARK	rgba(112, 25, 25, 255)
 	9	HUD_COLOUR_BLUE	rgba(93, 182, 229, 255)
 	10	HUD_COLOUR_BLUELIGHT	rgba(174, 219, 242, 255)
 	11	HUD_COLOUR_BLUEDARK	rgba(47, 92, 115, 255)
 	12	HUD_COLOUR_YELLOW	rgba(240, 200, 80, 255)
 	13	HUD_COLOUR_YELLOWLIGHT	rgba(254, 235, 169, 255)
 	14	HUD_COLOUR_YELLOWDARK	rgba(126, 107, 41, 255)
 	15	HUD_COLOUR_ORANGE	rgba(255, 133, 85, 255)
 	16	HUD_COLOUR_ORANGELIGHT	rgba(255, 194, 170, 255)
 	17	HUD_COLOUR_ORANGEDARK	rgba(127, 66, 42, 255)
 	18	HUD_COLOUR_GREEN	rgba(114, 204, 114, 255)
 	19	HUD_COLOUR_GREENLIGHT	rgba(185, 230, 185, 255)
 	20	HUD_COLOUR_GREENDARK	rgba(57, 102, 57, 255)
 	21	HUD_COLOUR_PURPLE	rgba(132, 102, 226, 255)
 	22	HUD_COLOUR_PURPLELIGHT	rgba(192, 179, 239, 255)
 	23	HUD_COLOUR_PURPLEDARK	rgba(67, 57, 111, 255)
 	24	HUD_COLOUR_PINK	rgba(203, 54, 148, 255)
 	25	HUD_COLOUR_RADAR_HEALTH	rgba(53, 154, 71, 255)
 	26	HUD_COLOUR_RADAR_ARMOUR	HUD_COLOUR_BLUE
 	27	HUD_COLOUR_RADAR_DAMAGE	rgba(235, 36, 39, 255)
 	28	HUD_COLOUR_NET_PLAYER1	rgba(194, 80, 80, 255)
 	29	HUD_COLOUR_NET_PLAYER2	rgba(156, 110, 175, 255)
 	30	HUD_COLOUR_NET_PLAYER3	rgba(255, 123, 196, 255)
 	31	HUD_COLOUR_NET_PLAYER4	rgba(247, 159, 123, 255)
 	32	HUD_COLOUR_NET_PLAYER5	rgba(178, 144, 132, 255)
 	33	HUD_COLOUR_NET_PLAYER6	rgba(141, 206, 167, 255)
 	34	HUD_COLOUR_NET_PLAYER7	rgba(113, 169, 175, 255)
 	35	HUD_COLOUR_NET_PLAYER8	rgba(211, 209, 231, 255)
 	36	HUD_COLOUR_NET_PLAYER9	rgba(144, 127, 153, 255)
 	37	HUD_COLOUR_NET_PLAYER10	rgba(106, 196, 191, 255)
 	38	HUD_COLOUR_NET_PLAYER11	rgba(214, 196, 153, 255)
 	39	HUD_COLOUR_NET_PLAYER12	rgba(234, 142, 80, 255)
 	40	HUD_COLOUR_NET_PLAYER13	rgba(152, 203, 234, 255)
 	41	HUD_COLOUR_NET_PLAYER14	rgba(178, 98, 135, 255)
 	42	HUD_COLOUR_NET_PLAYER15	rgba(144, 142, 122, 255)
 	43	HUD_COLOUR_NET_PLAYER16	rgba(166, 117, 94, 255)
 	44	HUD_COLOUR_NET_PLAYER17	rgba(175, 168, 168, 255)
 	45	HUD_COLOUR_NET_PLAYER18	rgba(232, 142, 155, 255)
 	46	HUD_COLOUR_NET_PLAYER19	rgba(187, 214, 91, 255)
 	47	HUD_COLOUR_NET_PLAYER20	rgba(12, 123, 86, 255)
 	48	HUD_COLOUR_NET_PLAYER21	rgba(123, 196, 255, 255)
 	49	HUD_COLOUR_NET_PLAYER22	rgba(171, 60, 230, 255)
 	50	HUD_COLOUR_NET_PLAYER23	rgba(206, 169, 13, 255)
 	51	HUD_COLOUR_NET_PLAYER24	rgba(71, 99, 173, 255)
 	52	HUD_COLOUR_NET_PLAYER25	rgba(42, 166, 185, 255)
 	53	HUD_COLOUR_NET_PLAYER26	rgba(186, 157, 125, 255)
 	54	HUD_COLOUR_NET_PLAYER27	rgba(201, 225, 255, 255)
 	55	HUD_COLOUR_NET_PLAYER28	rgba(240, 240, 150, 255)
 	56	HUD_COLOUR_NET_PLAYER29	rgba(237, 140, 161, 255)
 	57	HUD_COLOUR_NET_PLAYER30	rgba(249, 138, 138, 255)
 	58	HUD_COLOUR_NET_PLAYER31	rgba(252, 239, 166, 255)
 	59	HUD_COLOUR_NET_PLAYER32	rgba(240, 240, 240, 255)
 	60	HUD_COLOUR_SIMPLEBLIP_DEFAULT	rgba(159, 201, 166, 255)
 	61	HUD_COLOUR_MENU_BLUE	rgba(140, 140, 140, 255)
 	62	HUD_COLOUR_MENU_GREY_LIGHT	HUD_COLOUR_MENU_BLUE
 	63	HUD_COLOUR_MENU_BLUE_EXTRA_DARK	rgba(40, 40, 40, 255)
 	64	HUD_COLOUR_MENU_YELLOW	rgba(240, 160, 0, 255)
 	65	HUD_COLOUR_MENU_YELLOW_DARK	HUD_COLOUR_MENU_YELLOW
 	66	HUD_COLOUR_MENU_GREEN	HUD_COLOUR_MENU_YELLOW
 	67	HUD_COLOUR_MENU_GREY	rgba(140, 140, 140, 255)
 	68	HUD_COLOUR_MENU_GREY_DARK	rgba(60, 60, 60, 255)
 	69	HUD_COLOUR_MENU_HIGHLIGHT	rgba(30, 30, 30, 255)
 	70	HUD_COLOUR_MENU_STANDARD	rgba(140, 140, 140, 255)
 	71	HUD_COLOUR_MENU_DIMMED	rgba(75, 75, 75, 255)
 	72	HUD_COLOUR_MENU_EXTRA_DIMMED	rgba(50, 50, 50, 255)
 	73	HUD_COLOUR_BRIEF_TITLE	rgba(95, 95, 95, 255)
 	74	HUD_COLOUR_MID_GREY_MP	rgba(100, 100, 100, 255)
 	75	HUD_COLOUR_NET_PLAYER1_DARK	rgba(93, 39, 39, 255)
 	76	HUD_COLOUR_NET_PLAYER2_DARK	rgba(77, 55, 89, 255)
 	77	HUD_COLOUR_NET_PLAYER3_DARK	rgba(124, 62, 99, 255)
 	78	HUD_COLOUR_NET_PLAYER4_DARK	rgba(120, 80, 80, 255)
 	79	HUD_COLOUR_NET_PLAYER5_DARK	rgba(87, 72, 66, 255)
 	80	HUD_COLOUR_NET_PLAYER6_DARK	rgba(74, 103, 83, 255)
 	81	HUD_COLOUR_NET_PLAYER7_DARK	rgba(60, 85, 88, 255)
 	82	HUD_COLOUR_NET_PLAYER8_DARK	rgba(105, 105, 64, 255)
 	83	HUD_COLOUR_NET_PLAYER9_DARK	rgba(72, 63, 76, 255)
 	84	HUD_COLOUR_NET_PLAYER10_DARK	rgba(53, 98, 95, 255)
 	85	HUD_COLOUR_NET_PLAYER11_DARK	rgba(107, 98, 76, 255)
 	86	HUD_COLOUR_NET_PLAYER12_DARK	rgba(117, 71, 40, 255)
 	87	HUD_COLOUR_NET_PLAYER13_DARK	rgba(76, 101, 117, 255)
 	88	HUD_COLOUR_NET_PLAYER14_DARK	rgba(65, 35, 47, 255)
 	89	HUD_COLOUR_NET_PLAYER15_DARK	rgba(72, 71, 61, 255)
 	90	HUD_COLOUR_NET_PLAYER16_DARK	rgba(85, 58, 47, 255)
 	91	HUD_COLOUR_NET_PLAYER17_DARK	rgba(87, 84, 84, 255)
 	92	HUD_COLOUR_NET_PLAYER18_DARK	rgba(116, 71, 77, 255)
 	93	HUD_COLOUR_NET_PLAYER19_DARK	rgba(93, 107, 45, 255)
 	94	HUD_COLOUR_NET_PLAYER20_DARK	rgba(6, 61, 43, 255)
 	95	HUD_COLOUR_NET_PLAYER21_DARK	rgba(61, 98, 127, 255)
 	96	HUD_COLOUR_NET_PLAYER22_DARK	rgba(85, 30, 115, 255)
 	97	HUD_COLOUR_NET_PLAYER23_DARK	rgba(103, 84, 6, 255)
 	98	HUD_COLOUR_NET_PLAYER24_DARK	rgba(35, 49, 86, 255)
 	99	HUD_COLOUR_NET_PLAYER25_DARK	rgba(21, 83, 92, 255)
 	100	HUD_COLOUR_NET_PLAYER26_DARK	rgba(93, 98, 62, 255)
 	101	HUD_COLOUR_NET_PLAYER27_DARK	rgba(100, 112, 127, 255)
 	102	HUD_COLOUR_NET_PLAYER28_DARK	rgba(120, 120, 75, 255)
 	103	HUD_COLOUR_NET_PLAYER29_DARK	rgba(152, 76, 93, 255)
 	104	HUD_COLOUR_NET_PLAYER30_DARK	rgba(124, 69, 69, 255)
 	105	HUD_COLOUR_NET_PLAYER31_DARK	rgba(10, 43, 50, 255)
 	106	HUD_COLOUR_NET_PLAYER32_DARK	rgba(95, 95, 10, 255)
 	107	HUD_COLOUR_BRONZE	rgba(180, 130, 97, 255)
 	108	HUD_COLOUR_SILVER	rgba(150, 153, 161, 255)
 	109	HUD_COLOUR_GOLD	rgba(214, 181, 99, 255)
 	110	HUD_COLOUR_PLATINUM	rgba(166, 221, 190, 255)
 	111	HUD_COLOUR_GANG1	rgba(29, 100, 153, 255)
 	112	HUD_COLOUR_GANG2	rgba(214, 116, 15, 255)
 	113	HUD_COLOUR_GANG3	rgba(135, 125, 142, 255)
 	114	HUD_COLOUR_GANG4	rgba(229, 119, 185, 255)
 	115	HUD_COLOUR_SAME_CREW	rgba(252, 239, 166, 255)
 	116	HUD_COLOUR_FREEMODE	rgba(45, 110, 185, 255)
 	117	HUD_COLOUR_PAUSE_BG	rgba(0, 0, 0, 186)
 	118	HUD_COLOUR_FRIENDLY	rgba(93, 182, 229, 255)
 	119	HUD_COLOUR_ENEMY	rgba(194, 80, 80, 255)
 	120	HUD_COLOUR_LOCATION	HUD_COLOUR_YELLOW
 	121	HUD_COLOUR_PICKUP	HUD_COLOUR_GREEN
 	122	HUD_COLOUR_PAUSE_SINGLEPLAYER	HUD_COLOUR_GREEN
 	123	HUD_COLOUR_FREEMODE_DARK	rgba(22, 55, 92, 255)
 	124	HUD_COLOUR_INACTIVE_MISSION	rgba(154, 154, 154, 255)
 	125	HUD_COLOUR_DAMAGE	rgba(194, 80, 80, 255)
 	126	HUD_COLOUR_PINKLIGHT	rgba(252, 115, 201, 255)
 	127	HUD_COLOUR_PM_MITEM_HIGHLIGHT	rgba(252, 177, 49, 255)
 	128	HUD_COLOUR_SCRIPT_VARIABLE	rgba(0, 0, 0, 255)
 	129	HUD_COLOUR_YOGA	rgba(109, 247, 204, 255)
 	130	HUD_COLOUR_TENNIS	rgba(241, 101, 34, 255)
 	131	HUD_COLOUR_GOLF	rgba(214, 189, 97, 255)
 	132	HUD_COLOUR_SHOOTING_RANGE	HUD_COLOUR_REDDARK
 	133	HUD_COLOUR_FLIGHT_SCHOOL	HUD_COLOUR_BLUEDARK
 	134	HUD_COLOUR_NORTH_BLUE	HUD_COLOUR_BLUE
 	135	HUD_COLOUR_SOCIAL_CLUB	rgba(234, 153, 28, 255)
 	136	HUD_COLOUR_PLATFORM_BLUE	rgba(11, 55, 123, 255)
 	137	HUD_COLOUR_PLATFORM_GREEN	rgba(146, 200, 62, 255)
 	138	HUD_COLOUR_PLATFORM_GREY	rgba(234, 153, 28, 255)
 	139	HUD_COLOUR_FACEBOOK_BLUE	rgba(66, 89, 148, 255)
 	140	HUD_COLOUR_INGAME_BG	rgba(0, 0, 0, 186)
 	141	HUD_COLOUR_DARTS	HUD_COLOUR_GREEN
 	142	HUD_COLOUR_WAYPOINT	rgba(164, 76, 242, 255)
 	143	HUD_COLOUR_MICHAEL	rgba(101, 180, 212, 255)
 	144	HUD_COLOUR_FRANKLIN	rgba(171, 237, 171, 255)
 	145	HUD_COLOUR_TREVOR	rgba(255, 163, 87, 255)
 	146	HUD_COLOUR_GOLF_P1	HUD_COLOUR_WHITE
 	147	HUD_COLOUR_GOLF_P2	rgba(235, 239, 30, 255)
 	148	HUD_COLOUR_GOLF_P3	rgba(255, 149, 14, 255)
 	149	HUD_COLOUR_GOLF_P4	rgba(246, 60, 161, 255)
 	150	HUD_COLOUR_WAYPOINTLIGHT	rgba(210, 166, 249, 255)
 	151	HUD_COLOUR_WAYPOINTDARK	rgba(82, 38, 121, 255)
 	152	HUD_COLOUR_PANEL_LIGHT	rgba(0, 0, 0, 77)
 	153	HUD_COLOUR_MICHAEL_DARK	rgba(72, 103, 116, 255)
 	154	HUD_COLOUR_FRANKLIN_DARK	rgba(85, 118, 85, 255)
 	155	HUD_COLOUR_TREVOR_DARK	rgba(127, 81, 43, 255)
 	156	HUD_COLOUR_OBJECTIVE_ROUTE	HUD_COLOUR_YELLOW
 	157	HUD_COLOUR_PAUSEMAP_TINT	rgba(0, 0, 0, 215)
 	158	HUD_COLOUR_PAUSE_DESELECT	rgba(100, 100, 100, 127)
 	159	HUD_COLOUR_PM_WEAPONS_PURCHASABLE	HUD_COLOUR_FREEMODE
 	160	HUD_COLOUR_PM_WEAPONS_LOCKED	rgba(240, 240, 240, 191)
 	161	HUD_COLOUR_END_SCREEN_BG	HUD_COLOUR_INGAME_BG
 	162	HUD_COLOUR_CHOP	HUD_COLOUR_RED
 	163	HUD_COLOUR_PAUSEMAP_TINT_HALF	rgba(0, 0, 0, 215)
 	164	HUD_COLOUR_NORTH_BLUE_OFFICIAL	rgba(0, 71, 133, 255)
 	165	HUD_COLOUR_SCRIPT_VARIABLE_2	rgba(0, 0, 0, 255)
 	166	HUD_COLOUR_H	rgba(33, 118, 37, 255)
 	167	HUD_COLOUR_HDARK	rgba(37, 102, 40, 255)
 	168	HUD_COLOUR_T	rgba(234, 153, 28, 255)
 	169	HUD_COLOUR_TDARK	rgba(225, 140, 8, 255)
 	170	HUD_COLOUR_HSHARD	rgba(20, 40, 0, 255)
 	171	HUD_COLOUR_CONTROLLER_MICHAEL	rgba(48, 255, 255, 255)
 	172	HUD_COLOUR_CONTROLLER_FRANKLIN	rgba(48, 255, 0, 255)
 	173	HUD_COLOUR_CONTROLLER_TREVOR	rgba(176, 80, 0, 255)
 	174	HUD_COLOUR_CONTROLLER_CHOP	rgba(127, 0, 0, 255)
 	175	HUD_COLOUR_VIDEO_EDITOR_VIDEO	rgba(53, 166, 224, 255)
 	176	HUD_COLOUR_VIDEO_EDITOR_AUDIO	rgba(162, 79, 157, 255)
 	177	HUD_COLOUR_VIDEO_EDITOR_TEXT	rgba(104, 192, 141, 255)
 	178	HUD_COLOUR_HB_BLUE	rgba(29, 100, 153, 255)
 	179	HUD_COLOUR_HB_YELLOW	rgba(234, 153, 28, 255)
 	180	HUD_COLOUR_VIDEO_EDITOR_SCORE	rgba(240, 160, 1, 255)
 	181	HUD_COLOUR_VIDEO_EDITOR_AUDIO_FADEOUT	rgba(59, 34, 57, 255)
 	182	HUD_COLOUR_VIDEO_EDITOR_TEXT_FADEOUT	rgba(41, 68, 53, 255)
 	183	HUD_COLOUR_VIDEO_EDITOR_SCORE_FADEOUT	rgba(82, 58, 10, 255)
 	184	HUD_COLOUR_HEIST_BACKGROUND	rgba(37, 102, 40, 186)
 	185	HUD_COLOUR_VIDEO_EDITOR_AMBIENT	HUD_COLOUR_YELLOW
 	186	HUD_COLOUR_VIDEO_EDITOR_AMBIENT_FADEOUT	rgba(80, 70, 34, 255)
 	187	HUD_COLOUR_VIDEO_EDITOR_AMBIENT_DARK	HUD_COLOUR_ORANGE
 	188	HUD_COLOUR_VIDEO_EDITOR_AMBIENT_LIGHT	HUD_COLOUR_ORANGELIGHT
 	189	HUD_COLOUR_VIDEO_EDITOR_AMBIENT_MID	HUD_COLOUR_ORANGE
 	190	HUD_COLOUR_LOW_FLOW	HUD_COLOUR_YELLOW
 	191	HUD_COLOUR_LOW_FLOW_DARK	HUD_COLOUR_YELLOWDARK
 	192	HUD_COLOUR_G1	rgba(247, 159, 123, 255)
 	193	HUD_COLOUR_G2	rgba(226, 134, 187, 255)
 	194	HUD_COLOUR_G3	rgba(239, 238, 151, 255)
 	195	HUD_COLOUR_G4	rgba(113, 169, 175, 255)
 	196	HUD_COLOUR_G5	rgba(160, 140, 193, 255)
 	197	HUD_COLOUR_G6	rgba(141, 206, 167, 255)
 	198	HUD_COLOUR_G7	rgba(181, 214, 234, 255)
 	199	HUD_COLOUR_G8	rgba(178, 144, 132, 255)
 	200	HUD_COLOUR_G9	rgba(0, 132, 114, 255)
 	201	HUD_COLOUR_G10	rgba(216, 85, 117, 255)
 	202	HUD_COLOUR_G11	rgba(30, 100, 152, 255)
 	203	HUD_COLOUR_G12	rgba(43, 181, 117, 255)
 	204	HUD_COLOUR_G13	rgba(233, 141, 79, 255)
 	205	HUD_COLOUR_G14	rgba(137, 210, 215, 255)
 	206	HUD_COLOUR_G15	rgba(134, 125, 141, 255)
 	207	HUD_COLOUR_ADVERSARY	rgba(109, 34, 33, 255)
 	208	HUD_COLOUR_DEGEN_RED	rgba(255, 0, 0, 255)
 	209	HUD_COLOUR_DEGEN_YELLOW	rgba(255, 255, 0, 255)
 	210	HUD_COLOUR_DEGEN_GREEN	rgba(0, 255, 0, 255)
 	211	HUD_COLOUR_DEGEN_CYAN	rgba(0, 255, 255, 255)
 	212	HUD_COLOUR_DEGEN_BLUE	rgba(0, 0, 255, 255)
 	213	HUD_COLOUR_DEGEN_MAGENTA	rgba(255, 0, 255, 255)
 	214	HUD_COLOUR_STUNT_1	rgba(38, 136, 234, 255)
 	215	HUD_COLOUR_STUNT_2	HUD_COLOUR_RED
 	216	HUD_COLOUR_SPECIAL_RACE_SERIES	rgba(154, 178, 54, 255)
 	217	HUD_COLOUR_SPECIAL_RACE_SERIES_DARK	rgba(93, 107, 45, 255)
 	218	HUD_COLOUR_CS	rgba(206, 169, 13, 255)
 	219	HUD_COLOUR_CS_DARK	rgba(103, 84, 6, 255)
 	220	HUD_COLOUR_TECH_GREEN	rgba(0, 151, 151, 255)
 	221	HUD_COLOUR_TECH_GREEN_DARK	rgba(5, 119, 113, 255)
 	222	HUD_COLOUR_TECH_RED	rgba(151, 0, 0, 255)
 	223	HUD_COLOUR_TECH_GREEN_VERY_DARK	rgba(0, 40, 40, 255)
 	224	HUD_COLOUR_PLACEHOLDER_01	rgba(255, 255, 255, 255)
 	225	HUD_COLOUR_PLACEHOLDER_02	rgba(255, 255, 255, 255)
 	226	HUD_COLOUR_PLACEHOLDER_03	rgba(255, 255, 255, 255)
 	227	HUD_COLOUR_PLACEHOLDER_04	rgba(255, 255, 255, 255)
 	228	HUD_COLOUR_PLACEHOLDER_05	rgba(255, 255, 255, 255)
 	229	HUD_COLOUR_PLACEHOLDER_06	rgba(255, 255, 255, 255)
 	230	HUD_COLOUR_PLACEHOLDER_07	rgba(255, 255, 255, 255)
 	231	HUD_COLOUR_PLACEHOLDER_08	rgba(255, 255, 255, 255)
 	232	HUD_COLOUR_PLACEHOLDER_09	rgba(255, 255, 255, 255)
 	233	HUD_COLOUR_PLACEHOLDER_10	rgba(255, 255, 255, 255)
 	234	HUD_COLOUR_JUNK_ENERGY	rgba(29, 237, 195, 255)

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

Text formatting
Text labels displayed in the game UI can be formatted using classical Rockstar North-style ~ formatting tags, which are detailed below.

Rockstar formatting codes
Rockstar formatting codes are typically found between two tildes (~), such as in the following examples:

[MY_LABEL]
Demolish the ~r~enemy.

[MY_HELP_LABEL]
Press ~INPUT_CONTEXT~ when near the ~r~enemies.
Color codes
Special	Label	Description	Example
 	~HUD_COLOUR_...~	References an existing HUD color.	Find the ~HUD_COLOUR_FREEMODE~freemode ped!
 	~HC_...~	An alias for ~HUD_COLOUR	Find the ~HC_FREEMODE~freemode ped!
 	~HC_[number]~	Specifies a HUD color by index.	Get to ~HC_13~Davis.
 	~s~	Resets the color to the default for the current context.	After killing the ~r~enemies~s~, you win!
 	~v~	HUD_COLOUR_SCRIPT_VARIABLE
This is a placeholder for the color set with SET_SCRIPT_VARIABLE_HUD_COLOUR.	Wait for your ~v~team~s~ to lose the Cops.
 	~u~	HUD_COLOUR_SCRIPT_VARIABLE_2
This is a placeholder for the color set with _SET_SCRIPT_VARIABLE_2_HUD_COLOUR.	Take out ~v~~a~~s~ & defend ~u~~a~~s~.
 	~w~	HUD_COLOUR_WHITE
Used together with ~s~ to reset text color.	Swoop on over to ~b~foreclosures.maze-bank.com~w~~s~ today
Color	Label	Description	Example
 	~r~	HUD_COLOUR_RED
Used for enemy characters or vehicles.	Kill all the ~r~Vagos.
 	~g~	HUD_COLOUR_GREEN
Used for pickup-type objectives.	Pick up the ~g~flash drive.
 	~b~	HUD_COLOUR_BLUE
Used for friendly characters or vehicles.	Defend ~b~Lamar.
 	~f~	HUD_COLOUR_FRIENDLY
An alternate (rare) version for friendly objectives.	Vehicle health can be restored by waiting in the ~f~pit stop area~s~.
 	~y~	HUD_COLOUR_YELLOW
Destination names.	Deliver the Special Cargo to the ~y~restricted area.
 	~c~	HUD_COLOUR_MENU_GREY
De-emphasized text used in subtitles, to indicate a character out of view.	~z~He's a bum! ~c~~n~Oh my God!
 	~t~	HUD_COLOUR_MENU_GREY
De-emphasized text used in subtitles, to indicate text spoken in a different language.	~z~those ~t~idiots.
 	~o~	HUD_COLOUR_ORANGE
A team color indicator.	~o~The Cocks~s~ are mad.
 	~p~	HUD_COLOUR_PURPLE
A team color indicator.	~p~The Boars~s~ are off the radar.
 	~q~	HUD_COLOUR_PINK
Used for Arena War.	You are the active contender on your ~q~team~s~.
 	~m~	HUD_COLOUR_MID_GREY_MP
Medium gray to de-emphasize or use for 'Silver'.	~m~Display Mini Map.
 	~l~	HUD_COLOUR_BLACK
Used when unable to set a color any other way to specify black.	~l~PLAYERS
 	~d~	HUD_COLOUR_BLUEDARK
Used to specify a team objective occupied by a player.	Help your team deliver a ~d~vehicle ~s~to your ~b~base.
Visual formatting codes
Label	Description	Example
~n~	A line break, similar to <br> in HTML.	This text is~n~on two lines.
~h~	Bold text.
Use a second time to unbold.	This is ~h~quite bold~h~ of you.
~bold~	An alias of ~h~.	This is also pretty ~bold~bold~h~.
~italic~	Italic text.
Use a second time to remove italics.	Text can be ~italic~written~italic~ in italics.
~ws~	A wanted star.	The ~ws~~ws~ on the top right indicates
~wanted_star~	A wanted star, equal to ~ws~.	~wanted_star~~wanted_star~~wanted_star~
<C>...</C>	Condensed. Usually used for gamer tags.	<C>~a~</C> is dominating you.
~nrt~	Unknown.	
~EX_R*~	A Rockstar logo, in fonts that support this character.	The ~EX_R*~ logo is a registered trademark
~BLIP_...~	In help messages and other supported contexts, shows the blip with the specified name.	Benny's Original Motor Works is now available at ~HUD_COLOUR_YELLOW~~BLIP_BENNYS~~s~.
Content formatting codes
Label	Description	Example
~a~	A placeholder for a substring 'text component', such as ADD_TEXT_COMPONENT_SUBSTRING_TEXT_LABEL.	Fight the ~a~.
~1~	A placeholder for a numeric 'text component', such as ADD_TEXT_COMPONENT_INTEGER.	There are ~1~ enemies left.
~a_X~	For translations, refers to ~a~ placeholders out of the usual order.	Get the ~a_1~ from the ~a_0~.
~1_X~	For translations, refers to ~1~ placeholders out of the usual order.	There's ~1_1~ enemies left out of ~1_0~.
~x~	Unknown. Related to subtitles.	
~z~	At the start of a string, makes the string hidden if subtitles are turned off.	~z~Fucking terrorists. There's been a big scare
Input codes
Label	Description	Example
~INPUT_...~	In help messages and other supported contexts, shows the current key for a specified control.	Press ~INPUT_CONTEXT~ to stand up.
~INPUTGROUP_...~	In help messages and other supported contexts, shows a specified input group's hint.	If your car is upside down, try rocking ~INPUTGROUP_VEH_MOVE_ALL~ to flip it over.
~ACCEPT~	Shows the button to accept a prompt.	
~CANCEL~	Shows the button to cancel a prompt.	
~PAD_UP~	In supported contexts, shows a gamepad button or other control.	
~PAD_DOWN~	In supported contexts, shows a gamepad button or other control.	
~PAD_LEFT~	In supported contexts, shows a gamepad button or other control.	
~PAD_RIGHT~	In supported contexts, shows a gamepad button or other control.	
~PAD_A~	In supported contexts, shows a gamepad button or other control.	
~PAD_B~	In supported contexts, shows a gamepad button or other control.	
~PAD_X~	In supported contexts, shows a gamepad button or other control.	
~PAD_Y~	In supported contexts, shows a gamepad button or other control.	
~PAD_START~	In supported contexts, shows a gamepad button or other control.	
~PAD_BACK~	In supported contexts, shows a gamepad button or other control.	
~PAD_LB~	In supported contexts, shows a gamepad button or other control.	
~PAD_LT~	In supported contexts, shows a gamepad button or other control.	
~PAD_RB~	In supported contexts, shows a gamepad button or other control.	
~PAD_RT~	In supported contexts, shows a gamepad button or other control.	
~PAD_DPAD_UP~	In supported contexts, shows a gamepad button or other control.	
~PAD_DPAD_DOWN~	In supported contexts, shows a gamepad button or other control.	
~PAD_DPAD_LEFT~	In supported contexts, shows a gamepad button or other control.	
~PAD_DPAD_RIGHT~	In supported contexts, shows a gamepad button or other control.	
~PAD_DPAD_NONE~	In supported contexts, shows a gamepad button or other control.	
~PAD_DPAD_ALL~	In supported contexts, shows a gamepad button or other control.	
~PAD_DPAD_UPDOWN~	In supported contexts, shows a gamepad button or other control.	
~PAD_DPAD_LEFTRIGHT~	In supported contexts, shows a gamepad button or other control.	
~PAD_LSTICK_UP~	In supported contexts, shows a gamepad button or other control.	
~PAD_LSTICK_DOWN~	In supported contexts, shows a gamepad button or other control.	
~PAD_LSTICK_LEFT~	In supported contexts, shows a gamepad button or other control.	
~PAD_LSTICK_RIGHT~	In supported contexts, shows a gamepad button or other control.	
~PAD_LSTICK_NONE~	In supported contexts, shows a gamepad button or other control.	
~PAD_LSTICK_ALL~	In supported contexts, shows a gamepad button or other control.	
~PAD_LSTICK_UPDOWN~	In supported contexts, shows a gamepad button or other control.	
~PAD_LSTICK_LEFTRIGHT~	In supported contexts, shows a gamepad button or other control.	
~PAD_LSTICK_ROTATE~	In supported contexts, shows a gamepad button or other control.	
~PAD_RSTICK_UP~	In supported contexts, shows a gamepad button or other control.	
~PAD_RSTICK_DOWN~	In supported contexts, shows a gamepad button or other control.	
~PAD_RSTICK_LEFT~	In supported contexts, shows a gamepad button or other control.	
~PAD_RSTICK_RIGHT~	In supported contexts, shows a gamepad button or other control.	
~PAD_RSTICK_NONE~	In supported contexts, shows a gamepad button or other control.	
~PAD_RSTICK_ALL~	In supported contexts, shows a gamepad button or other control.	
~PAD_RSTICK_UPDOWN~	In supported contexts, shows a gamepad button or other control.	
~PAD_RSTICK_LEFTRIGHT~	In supported contexts, shows a gamepad button or other control.	
~PAD_RSTICK_ROTATE~	In supported contexts, shows a gamepad button or other control.

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------


-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
