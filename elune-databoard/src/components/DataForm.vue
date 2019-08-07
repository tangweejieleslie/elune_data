<template>
  <v-container>
    <v-layout text-center wrap>
      <v-flex>
        <h1>Data entry</h1>
        <v-form>
          <v-text-field  v-model="userdata.name"> 
              {{ userdata.name }} 
          </v-text-field>
          <v-autocomplete label="Grade" :items="grade" v-model="userdata.grade">
              {{ userdata.grade }}
          </v-autocomplete>
        </v-form>
        <v-btn 
            v-on:click="submit"
        >
            Console Log Results
        </v-btn>
        {{ computedDamage }}
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    userdata: {
        name: "",
        grade: ""
    },  
    name: "",
    grade: ["Legendary", "Epic", "Rare", "Uncommon", "Normal"],
    elune_class: ["Tank", "DPS", "Healer", "Support", "Debuffer"],
    level: [10, 20, 30, 40, 50, 60],
    stars: [1, 2, 3, 4, 5, 6],
    ascend: [1, 2, 3, 4, 5],
    stats: {
      hp: 0,
      atk: 10,
      pdef: 0,
      mdef: 0,
      atkspd: 0,
      acc: 0,
      eva: 0,
      crt: 0,
      crtpow: 0
    },
    skill: { 
      type: ["Normal", "Special", "Ultimate"],
      soul_cost: [0, 4, 6],
      targets: ["Front first", "All enemies"],
      multi_hits: 1, // number of hits
      damage_variables: {
        fixed: 100,
        MultiplyByAtk: 1.1
      },
      effects_template: {
        effect_type: ["physical", "nature", "spell", "curse", "weakening"],
        effect_name: "",
        activation_chance: 0.0,
        activation_condition: "",
        effect_turns: 0,
        effect_desc: ""
      },
      effects: [] // add additional effects per skill based on template
    },
    effects: {
      physical: {
        stun: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc: "Prevents Actions."
        },
        provoke: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc:
            "Can only attack the caster using a normal skill (Skill targeting allies are disabled)."
        },
        paralysis: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc: "Prevents actions + All damage taken is CRT damage."
        },
        blind: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc:
            "Skills targeting allies are disabled + Attacks targeting enemies miss."
        },
        bleeding: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc:
            "Receives Soul Damage equal to 8% of Max HP when receiving a turn."
        }
      },
      nature: {
        poison: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc:
            "Soul Damage equal to 50% of the caster's ATK when receiving a turn."
        },
        blaze: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc: "Soul Damage equal to 15% of current HP when receiving a turn."
        },
        frostbite: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc:
            "Soul Damage equal to 50% of the caster's ATK when receiving a turn."
        },
        freeze: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc: "Prevents actions + 5% additional damage per hit if hit."
        },
        epidemic: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc:
            "Increases a skill's SOUL consumption by 1 + infects nearby allies at the end of a turn."
        }
      },
      spell: {
        seal: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc: "Disables skills that consume SOUL."
        },
        confuse: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc:
            "Control of unit disabled + Unit sees friends as foes, and foes as friends."
        },
        banish: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc: "Prevents actions + Immune to damage and effects."
        },
        charm: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc:
            "Prevents actions + Gives SOUL or Rage to caster when receiving a turn."
        },
        restrain: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc: "Prevents actions + Moved to end of turn order."
        }
      },
      curse: {
        despair: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc: "Unable to receive any buffs."
        },
        petrify: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc:
            "Prevents actions + Soul Damage equal to 10% of MAX HP if hit + Immune to all status effects."
        },
        panic: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc: "SOUL or Rage disappears when receiving a turn (Up to 3)."
        },
        sleep: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc:
            "Prevents actions (Removed if hit) + 50% more damage for first hit if hit."
        },
        zombie: {
          activation_chance: 0.0,
          effect_turns: 0,
          desc: "Soul Damage based on Healing Received."
        }
      }
    }
  }),
  methods: {
      submit(){
          console.log(this.userdata);
          
      }
  },
  computed: {
    computedDamage(){
        return this.skill.damage_variables.fixed + this.skill.damage_variables.MultiplyByAtk * this.stats.atk;
    } 
  }
};
</script>
