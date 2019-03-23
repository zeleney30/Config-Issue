local w, h = client.screen_size()

local cfgIssueCheckbox = ui.new_checkbox("Visuals", "Other ESP", "Config issue")
local cfgIssueColor = ui.new_color_picker("Visuals", "Other ESP", "Config issue")
local cfgIssueDuration = ui.new_slider("Visuals", "Other ESP", "Duration", 1, 9, 3)

local miss = 0

local function set0()
	miss = 0
end

local function on_aim_miss(e)
	miss = 1
	client.delay_call(ui.get(cfgIssueDuration), set0)
end

client.set_event_callback('aim_miss', on_aim_miss)

local function on_paint(ctx)
	local r, g, b, a = ui.get(cfgIssueColor)
	if ui.get(cfgIssueCheckbox, true) then
		ui.set_visible(cfgIssueColor, true)
		ui.set_visible(cfgIssueDuration, true)

		if miss == 1 then
			renderer.text(w / 2, h / 2, r, g, b, a, "c+", 0, "cfg issue")
		end
	else
		ui.set_visible(cfgIssueColor, false)
		ui.set_visible(cfgIssueDuration, false)
	end
end

client.set_event_callback('paint', on_paint)
