<template>
  <div class="demo button-demo">
    <h2>{{ translate("title.basic") }}</h2>
    <quark-cell-group>
      <quark-cell
        type="primary"
        :title="translate('cellTitle.single')"
        :desc="formatFullDate(state.date.selectSingle)"
        islink
        @click="open('single', 'selectSingle')"
      ></quark-cell>
      <quark-cell
        type="primary"
        :title="translate('cellTitle.multiple')"
        :desc="formatMultiple(state.date.selectMultiple)"
        islink
        @click="open('multiple', 'selectMultiple')"
      ></quark-cell>
      <quark-cell
        type="primary"
        :title="translate('cellTitle.range')"
        :desc="formatRange(state.date.selectRange)"
        islink
        @click="open('range', 'selectRange')"
      ></quark-cell>
    </quark-cell-group>
    <h2>{{ translate("title.quick") }}</h2>
    <quark-cell-group>
      <quark-cell
        type="primary"
        :title="translate('cellTitle.single')"
        :desc="formatFullDate(state.date.quickSelectSingle)"
        islink
        @click="open('single', 'quickSelectSingle')"
      ></quark-cell>
      <quark-cell
        type="primary"
        :title="translate('cellTitle.range')"
        :desc="formatRange(state.date.quickSelectRange)"
        islink
        @click="open('range', 'quickSelectRange')"
      ></quark-cell>
    </quark-cell-group>
    <h2>{{ translate("title.custom") }}</h2>
    <quark-cell-group>
      <quark-cell
        type="primary"
        :title="translate('cellTitle.customDefault')"
        :desc="formatFullDate(state.date.customDefault)"
        islink
        @click="open('single', 'customDefault')"
      ></quark-cell>
      <quark-cell
        type="primary"
        :title="translate('cellTitle.customRange')"
        :desc="formatFullDate(state.date.customRange)"
        islink
        @click="open('single', 'customRange')"
      ></quark-cell>
      <quark-cell
        type="primary"
        :title="translate('cellTitle.customMaxRange')"
        :desc="formatRange(state.date.customMaxRange)"
        islink
        @click="open('range', 'customMaxRange')"
      ></quark-cell>
      <quark-cell
        type="primary"
        :title="translate('cellTitle.customConfirm')"
        :desc="formatRange(state.date.customConfirm)"
        islink
        @click="open('range', 'customConfirm')"
      ></quark-cell>
      <quark-cell
        type="primary"
        :title="translate('cellTitle.customDayText')"
        :desc="formatRange(state.date.customDayText)"
        islink
        @click="open('range', 'customDayText')"
      ></quark-cell>
      <quark-cell
        type="primary"
        :title="translate('cellTitle.weekFirstDay')"
        :desc="formatFullDate(state.date.weekFirstDay)"
        islink
        @click="open('single', 'weekFirstDay')"
      ></quark-cell>
      <quark-cell
        type="primary"
        :title="translate('cellTitle.customPosition')"
        :desc="formatFullDate(state.date.customPosition)"
        islink
        @click="open('single', 'customPosition')"
      ></quark-cell>
      <quark-cell
        type="primary"
        :title="translate('cellTitle.customCss')"
        :desc="formatFullDate(state.date.customCss)"
        islink
        @click="open('single', 'customCss')"
      ></quark-cell>
    </quark-cell-group>
    <h2>{{ translate("title.tiled") }}</h2>
    <quark-calendar
      :tiled="true"
      :maxdate="state.tiledMaxDate"
      :mindate="state.tiledMinDate"
      hideconfirm
      false
    >
    </quark-calendar>
    <quark-calendar
      :class="state.isCss ? 'custom-css' : ''"
      ref="calendarRef"
      :open="state.visible"
      :type="state.type"
      :round="state.round"
      :position="state.position"
      :mindate="state.minDate"
      :maxdate="state.maxDate"
      :maxrange="state.maxRange"
      :formatter="state.formatter"
      :hideconfirm="state.hideConfirm"
      :confirmtext="state.confirmText"
      :weekfirstday="state.weekFirstDay"
      :confirmdisabledtext="state.confirmDisabledText"
      @close="close"
      @confirm="({ detail }) => confirm(detail)"
    >
    </quark-calendar>
  </div>
</template>
<script>
import { onBeforeMount } from "vue";
import { createComponent } from "@/utils/create";
const { createDemo, translate } = createComponent("calendar");
import { useTranslate } from "@/sites/assets/util/useTranslate";
import { ref, reactive } from "vue";

export default createDemo({
  setup() {
    onBeforeMount(() => {
      useTranslate({
        "zh-CN": {
          title: {
            basic: "基础用法",
            quick: "快捷选择",
            custom: "自定义日历",
            tiled: "平铺展示",
          },
          cellTitle: {
            single: "选择单个日期",
            multiple: "选择多个日期",
            range: "选择日期区间",
            customDefault: "自定义选中值",
            customMaxRange: "日期区间最大范围",
            customRange: "自定义日期范围",
            customConfirm: "自定义按钮文字",
            customDayText: "自定义日期文案",
            customPosition: "自定义弹出位置",
            customCss: "自定义样式",
            weekFirstDay: "自定义周起始日",
          },
          otherText: {
            multiple: "个日期",
            confirmText: "完成",
            confirmDisabledText: "请选择",
            midAutumn: "中秋节",
            nationalDday: "国庆节",
            today: "今天",
            rest: "休",
            in: "入店",
            out: "离店",
          },
        },
        "en-US": {
          title: {
            basic: "Basic Usage",
            quick: "Quick Select",
            custom: "Custom Calendar",
            tiled: "Tiled display",
          },
          cellTitle: {
            single: "Select Single Date",
            multiple: "Select Multiple Date",
            range: "Select Date Range",
            customDefault: "Custom Selected Value",
            customMaxRange: "Custom The Maximum Number Of Selected Days",
            customRange: "Custom Date Range",
            customConfirm: "Custom Confirm Text",
            customDayText: "Custom Day Text",
            customPosition: "Custom Pop Position",
            customCss: "Custom CSS",
            weekFirstDay: "Custom First Day Of Week",
          },
          otherText: {
            multiple: "Dates",
            confirmText: "OK",
            confirmDisabledText: "Please Select",
            midAutumn: "Mid-Autumn",
            nationalDday: "National Day",
            today: "Today",
            rest: "Rest",
            in: "In",
            out: "Out",
          },
        },
      });
    });

    const state = reactive({
      date: {
        selectSingle: null,
        selectRange: [],
        selectMultiple: [],
        quickSelectSingle: null,
        quickSelectRange: [],
        customDefault: new Date(),
        customConfirm: [],
        customRange: null,
        customMaxRange: [],
        customDayText: [],
        weekFirstDay: null,
        customPosition: null,
        customCss: null,
      },
      isCss: false,
      visible: false,
      type: "single",
      round: true,
      minDate: undefined,
      maxDate: undefined,
      tiledMinDate: "2023-09-01",
      tiledMaxDate: "2023-10-31",
      maxRange: undefined,
      position: undefined,
      formatter: undefined,
      hideConfirm: false,
      confirmText: undefined,
      confirmDisabledText: undefined,
      weekFirstDay: 0,
    });

    const calendarRef = ref(null);

    const resetSettings = () => {
      state.round = true;
      state.minDate = undefined;
      state.maxDate = undefined;
      state.maxRange = undefined;
      state.position = undefined;
      state.formatter = undefined;
      state.hideConfirm = false;
      state.confirmText = undefined;
      state.confirmDisabledText = undefined;
      state.weekFirstDay = 0;
      state.isCss = false;
      calendarRef.value.setValue(null);
    };
    const dayFormatter = (day) => {
      if (!day.date) {
        return day;
      }

      const month = day.date.getMonth() + 1;
      const date = day.date.getDate();

      if (month === 9) {
        if (date === 29) {
          day.topInfo = translate("otherText.midAutumn");
        }
        if (date === 10) {
          day.topInfo = translate("otherText.today");
        }
        if (date > 28) {
          day.bottomInfo = translate("otherText.rest");
        }
      }

      if (month === 10) {
        if (date === 1) {
          day.topInfo = translate("otherText.nationalDday");
        }
        if (date < 7) {
          day.bottomInfo = translate("otherText.rest");
        }
      }

      if (day.type === "start") {
        day.bottomInfo = translate("otherText.in");
      } else if (day.type === "end") {
        day.bottomInfo = translate("otherText.out");
      }

      return day;
    };

    const open = (type, id) => {
      resetSettings();
      state.id = id;
      state.type = type;
      state.visible = true;
      switch (id) {
        case "quickSelectSingle":
        case "quickSelectRange":
          state.hideConfirm = true;
          break;
        case "customDefault":
          calendarRef.value.setValue(new Date());
          break;
        case "customConfirm":
          state.confirmText = translate("otherText.confirmText");
          state.confirmDisabledText = translate(
            "otherText.confirmDisabledText"
          );
          break;
        case "customRange":
          state.minDate = "2022-1-1";
          state.maxDate = "2022-1-31";
          break;
        case "customDayText":
          state.minDate = "2023-9-15";
          state.maxDate = "2023-10-15";
          calendarRef.value.setFormatter(dayFormatter);
          break;
        case "customPosition":
          state.round = false;
          state.position = "right";
          break;
        case "customMaxRange":
          state.maxRange = 3;
          break;
        case "weekFirstDay":
          state.weekFirstDay = 1;
          break;
        case "customCss":
          state.isCss = true;
          break;
      }
    };

    const formatDate = (date) => {
      if (date) {
        return `${date.getMonth() + 1}/${date.getDate()}`;
      }
    };
    const formatFullDate = (date) => {
      if (date) {
        return `${date.getFullYear()}/${formatDate(date)}`;
      }
    };

    const formatMultiple = (dates) => {
      if (dates.length) {
        let text = translate("otherText.multiple");
        if (dates.length === 1 && text.match(/.+s$/)) {
          text = text.slice(0, text.length - 1);
        }
        return dates.length + text;
      }
    };

    const formatRange = (dateRange) => {
      if (dateRange.length) {
        const [start, end] = dateRange;
        return `${formatDate(start)} - ${formatDate(end)}`;
      }
    };

    const confirm = ({ value }) => {
      state.visible = false;
      state.date[state.id] = value;
    };

    const close = () => {
      state.visible = false;
    };

    return {
      translate,
      state,
      calendarRef,
      resetSettings,
      open,
      close,
      confirm,
      formatFullDate,
      formatMultiple,
      formatRange,
    };
  },
});
</script>
<style src="./demo.scss"></style>
